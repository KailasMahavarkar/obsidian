## Semaphores
When you have requirement of synchronization, for example imagine you have multiple threads like t1, t2, t3, t4 and they are not trying to acquire same resource but there is some kind of dependency which must hold valid if we want to get correct results from program.

> Its similar in way of promises where one promise finishes and then other starts (a signal was sent from one to other) and other callback listened to that promise status (key diff here is that, we expected the promise is always resolvable)

Example: order of execution
```
t1 
t2 
t3 

// see the syncronization (inter-dependecy between threads)
t2 depends on t1 (until then its blocked)
& t3 depends on t2 (until then its blocked)
```

Being dependable on other thread is the key difference (in mutex all try to acquire same resource so a single lock is used there)


## Mutexes

Mutex is a lock in very simple terms, so if we many threads with no synchronization between them like all of them are racing to acquire same resource and only one can have it at a time then we use mutexes

How are mutexes implemented?
In `JS` or `Python` you can implement basic mutexes using queue and promises.

mutexes: `lock mechanism`
semaphore: `signaling mechanism`

