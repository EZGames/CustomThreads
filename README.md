# CustomThreads
A small library to help build Runnables and Callables that tweak the threads that they're run in to make debugging easier and to customize their use.

Features a decorative, fluent way to customize your threads in the following way:
+ Name your threads
+ Give your threads a priority
+ Assign an exception handler to the thread
+ Set the thread as a daemon thread

All of these features reset to the previous settings once the Callable or Runnable is finished.

To use the library, you start by creating an ExtendableCallable or ExtendableRunnable, passing in your Callable or Runnable:
```java
ExtendableCallable myCallable = new ExtendableCallable(() -> longReturningProcess());
//or
ExtendableRunnable myRunnable = new ExtendableRunnable(() -> longProcess());
```
Afterwards, to do any customizations, call one of their methods (other than call() or run()). For example, you can set the thread's priority and name like this:
```java
myCallable.withPriority(3).withThreadName("My Awesome Callable Thread");
myRunnable.withPriority(3).withThreadName("My Awesome Runnable Thread");
```
Other thread modifications include `asDaemon()` and `withExceptionHandling(UncaughtExceptionHandler)`.

ExtendableCallable and ExtendableRunanble implement the Callable and Runnable interfaces, respectively, so they can be passed into anything that takes a Callable or Runnable.

NOTE: documentation and testing not completed
