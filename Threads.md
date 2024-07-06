# Threads
#### Rust threading is portable, so following code should work Mac, Linux, and Windows. It will also work on whole bunch of other platforms.

```rust
use std::thread;

fn main() {
    let handle = thread::spawn(move || {
        // do stuff in a child thread.
    });

    // do stuff in the main thread.

    // wait until thread has exited.
    handle.join().unwrap();
}
```

- `thread::spawn` creates a new thread and returns a `JoinHandle` which can be used to wait for the thread to finish.
- `thread::spawn` takes a closure with no arguments. This closure is executed as the main function of the thread. Anything we want to do in the thread should be inside this closure. Usually we call a function from the closure.
- `.join()` waits for the thread to finish. It returns a `Result` which we can unwrap to get the result of the thread. If the thread panics, `join` will return an `Err` with the panic message.
- Threading is a bit heavyweight. Spawning a thread requires reserving some memory in RAM for its own stack, usually a couple of megabytes.
- Whenever a CPU switches from running one thread to another, it has to do a expensive context switch. So the more threads you have trying to access the CPU core, more overhead you will have during context switches.
- Threads are fantastic tool when you need to use CPU and thread concurrently.
- Because they can run simultaneously on multiple cores and actually accomplish more work.
- But if you are doing I/O bound work, like reading from disk, network, or database, you should use async/await instead of threads.
