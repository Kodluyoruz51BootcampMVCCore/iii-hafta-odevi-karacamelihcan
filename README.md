# III-hafta-odevi


1.Task vs process- task vs Thread vs .. ve c# task vs thread vs .. kıyaslamalarını ve task haricinde diğer yöntemler nelerdir araştırınız.
2.Extension Nedir? --> Extra paket ekleme. <br/>
3.SQLite, bunu doğru şekilde (en güncel yol ile) nasıl kullanmalıyız? (Aktif halde kullanıp uygulama)

## Task ve Thread Nedir in c#

Thread is a lower-level concept: if you're directly starting a thread, you know it will be a separate thread, rather than executing on the thread pool etc. Task is more than just an abstraction of "where to run some code" though - it's really just "the promise of a result in the future". So as some different examples: [Source](https://www.c-sharpcorner.com/article/task-and-thread-in-c-sharp/#:~:text=Differences%20Between%20Task%20And%20Thread,-Here%20are%20some&text=The%20Thread%20class%20is%20used%20for%20creating%20and%20manipulating%20a,tasks%20asynchronously%20and%20in%20parallel.&text=Threads%20can%20only%20have%20one%20task%20running%20at%20a%20time.)

## Task vs Process in c# 
A procedure is a synonym for a task, but a process is an upper level series of major steps, with those major steps being procedures or tasks. Tasks are made up of actions or steps.

A process is an upper level description of a series of major steps required to accomplish an objective. Processes are generally made up of procedures or tasks. A task is another way of describing a procedure. Another way of putting it is that a process is a sequence of tasks.

DITA does not distinguish between processes and tasks, although DITA 1.2 does provide strict task and general task variants of the task information type.

The term task is used in DITA, in preference to procedure, work instruction or unit rule. A task topic contains one procedure or task, and is made up of a series of steps. In turn, steps are made up of commands (or actions), step results, and perhaps substeps.

In a process, each step outlines the result or outcome of a task, and that step is typically linked to the task topic that details that step at a lower level.

## Task vs ValueTask in c# 
Methods may return an instance of this value type when it's likely that the result of their operations will be available synchronously and when the method is expected to be invoked so frequently that the cost of allocating a new Task<TResult> for each call will be prohibitive.

There are tradeoffs to using a ValueTask<TResult> instead of a Task<TResult>. For example, while a ValueTask<TResult> can help avoid an allocation in the case where the successful result is available synchronously, it also contains two fields whereas a Task<TResult> as a reference type is a single field. This means that a method call ends up returning two fields worth of data instead of one, which is more data to copy. It also means that if a method that returns one of these is awaited within an async method, the state machine for that async method will be larger due to needing to store the struct that's two fields instead of a single reference.

Further, for uses other than consuming the result of an asynchronous operation via await, ValueTask<TResult> can lead to a more convoluted programming model, which can in turn actually lead to more allocations. For example, consider a method that could return either a Task<TResult> with a cached task as a common result or a ValueTask<TResult>. If the consumer of the result wants to use it as a Task<TResult>, such as to use with in methods like Task.WhenAll and Task.WhenAny, the ValueTask<TResult> would first need to be converted into a Task<TResult> using AsTask, which leads to an allocation that would have been avoided if a cached Task<TResult> had been used in the first place.

As such, the default choice for any asynchronous method should be to return a Task or Task<TResult>. Only if performance analysis proves it worthwhile should a ValueTask<TResult> be used instead of Task<TResult>.
  
## Extentations 
Methods may return an instance of this value type when it's likely that the result of their operations will be available synchronously and when the method is expected to be invoked so frequently that the cost of allocating a new Task<TResult> for each call will be prohibitive.

There are tradeoffs to using a ValueTask<TResult> instead of a Task<TResult>. For example, while a ValueTask<TResult> can help avoid an allocation in the case where the successful result is available synchronously, it also contains two fields whereas a Task<TResult> as a reference type is a single field. This means that a method call ends up returning two fields worth of data instead of one, which is more data to copy. It also means that if a method that returns one of these is awaited within an async method, the state machine for that async method will be larger due to needing to store the struct that's two fields instead of a single reference.

Further, for uses other than consuming the result of an asynchronous operation via await, ValueTask<TResult> can lead to a more convoluted programming model, which can in turn actually lead to more allocations. For example, consider a method that could return either a Task<TResult> with a cached task as a common result or a ValueTask<TResult>. If the consumer of the result wants to use it as a Task<TResult>, such as to use with in methods like Task.WhenAll and Task.WhenAny, the ValueTask<TResult> would first need to be converted into a Task<TResult> using AsTask, which leads to an allocation that would have been avoided if a cached Task<TResult> had been used in the first place.

As such, the default choice for any asynchronous method should be to return a Task or Task<TResult>. Only if performance analysis proves it worthwhile should a ValueTask<TResult> be used instead of Task<TResult>.

## SQLite, bunu doğru şekilde (en güncel yol ile) nasıl kullanmalıyız?
https://stackoverflow.com/questions/59284020/how-do-i-properly-use-my-sqlite-db-in-my-asp-net-core-3-1-mvc-application-using
