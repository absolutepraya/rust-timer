## Understanding What's Happening

![Print Outside Spawn](./images/1.png)

When the program runs, the first output you see is `hey hey`. This happens because the corresponding print statement is executed as part of the main function’s regular, synchronous flow—before any async tasks are handled.

The other two messages, "howdy!" and "done!", are generated inside an async block that is submitted to the executor. These messages are not printed right away. Instead, they appear only after the following sequence: the main function’s synchronous code finishes, the spawner is dropped (indicating no more tasks will be added), and finally, `executor.run()` is called to process the async tasks.

This sequence highlights a fundamental aspect of async programming: tasks spawned asynchronously are not executed immediately. They remain pending until the executor is explicitly told to process them, which happens after the synchronous code has run.