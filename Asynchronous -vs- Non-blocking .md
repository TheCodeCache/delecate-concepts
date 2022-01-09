- `Asynchronous` refers to something done in parallel, say is another thread.
- `Non-blocking` often refers to polling,  
i.e. checking whether given condition holds (socket is readable, device has more data, etc.)  

Here is a typical example about `non-blocking & synchronous`:  
```java
// thread X
while (true)
{
    msg = recv(Y, NON_BLOCKING_FLAG);
    if (msg is not empty)
    {
        break;
    }
    else
    {
        sleep(2000); // 2 sec
    }
}

// thread Y
// prepare the book for X
send(X, book);
```

1. `blocking`: 
before Y answers X, X keeps waiting there for the answer.  
Now X (one module) is blocking.  
X and Y are two threads or two processes or one thread or one process? we DON'T know.  

2. `non-blocking`: 
before Y answers X, X just leaves there and do other things.  
X may come back every two minutes to check if Y has finished its job? Or X won't come back until Y calls him?  
We don't know. We only know that X can do other things before Y finishes its job.  
Here X (one module) is non-blocking. X and Y are two threads or two processes or one process? we DON'T know.  
BUT we are sure that X and Y couldn't be one thread.  

3. `synchronous`: 
before Y answers X, X keeps waiting there for the answer.  
It means that X can't continue until Y finishes its job. Now we say: X and Y (two modules) are synchronous.  
X and Y are two threads or two processes or one thread or one process? we DON'T know.  

4. `asynchronous`: 
before Y answers X, X leaves there and X can do other jobs. X won't come back until Y calls him.  
Now we say: X and Y (two modules) are asynchronous.  
X and Y are two threads or two processes or one process? we DON'T know.  
BUT we are sure that X and Y couldn't be one thread.  

https://stackoverflow.com/a/31298006/6842300

![image](https://user-images.githubusercontent.com/26399543/148696110-39934a92-537d-4006-9734-28d3a245d7ef.png)  


**Reference:**  
1. https://stackoverflow.com/a/31298006/6842300
2. https://stackoverflow.com/a/2625569/6842300
3. https://en.wikipedia.org/wiki/Asynchronous_I/O

