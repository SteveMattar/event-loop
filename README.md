# event-loop
## Callback execution order
On each iteration of the event loop callbacks are run in the following order:

![alt text](http://dfmonaco.com/images/posts/node_event_loop.svg "node event loop")

1. Run initial script

* -> Run Next Tick callbacks.

2. Run Timer callbacks: All active timers scheduled for a time before the loop’s concept of now get their callbacks called.

* -> Run Next Tick callbacks.

3. Run Pending I/O callbacks: If the previous iteration deferred any I/O callback it will be run at this point.

* -> Run Next Tick callbacks.

4. Run Current I/O callbacks: At this point the loop will block for I/O (with a previously calculated timeout), all I/O related handles that were monitoring a given file descriptor for a read or write operation get their callbacks called at this point.

* -> Run Next Tick callbacks.

5. Run Immediate callbacks: The entire callback queue is processed every event loop iteration.

* -> Run Next Tick callbacks.

6. Go to step 2: Start new cycle
