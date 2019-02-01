# Async/await

- you can also await the result of a non-async method that returns Task
- A non-async method returning Task.FromResult is more efficient than an async method returning a value.
- Async methods can return Task<T>, Task, or void. In almost all cases, you want to return Task<T> or Task, and return void only when you have to.
- Remember that async is an implementation detail, so interfaces can’t be defined with async. To define an asynchronous method in an interface, you just need to define a method with the same signature, minus the async keyword:
- The bottom line is that async constructors are not allowed, so let’s explore some alternatives.
- 


### Why async designed like this
[The Async CTP "Why Do the Keywords Work THAT Way" Unofficial FAQ](https://blog.stephencleary.com/2011/09/async-ctp-why-do-keywords-work-that-way.html)

[Dixin's Blog - Understanding C# async / await (3) Runtime Context](https://weblogs.asp.net/dixin/understanding-c-sharp-async-await-3-runtime-context)

[Await, SynchronizationContext, and Console Apps \| Parallel Programming with .NET](https://blogs.msdn.microsoft.com/pfxteam/2012/01/20/await-synchronizationcontext-and-console-apps/)
- Why not return int
  - Async methods that return a value must have an actual result type of Task<TResult>. So GetValue will show up in IntelliSense as returning Task<TResult> (this would also be true for the object browser, Reflector, etc).

### Context

### Call async from sync
- Task.WaitAndUnwrapException
- every await in MyAsyncMethod should end with ConfigureAwait(false)

