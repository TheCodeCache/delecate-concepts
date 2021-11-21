# Connection-less protocol
- It is like `post-office` system, where we just send the posts but never receives the acknowledgement.  
- `UDP` is one such protocol which uses `connection-less` protocol to transmit data over the n/w.  
- It is `faster`.
- it should only be used when `speed is more important the delivery` of the message.  
- We should ideally not use this protocol to build our services or applications  
- Congestion is possible.
- N/W packets do not follow the same route  
- Requires `less bandwidth`  
- Should be preferred for `bursty` communication  
- `No Authentication` is required  

    ![image](https://user-images.githubusercontent.com/26399543/142746354-466ebd4d-46ec-448b-9911-d0114b76cc0f.png)


# Connection-oriented protocol
- It is like `telephone` system, where we first establish the connection and then transfer the information.  
- `TCP` is one such protocol which uses `connection-oriented` protol to transit data over the n/w.  
- It is `slower`.
- It should only be used when `delivery is more important than the speed` of the message.  
- We should ideally use this protocol to build our services or applications  
- Congestion is not possible.  
- N/W packets follow the same route  
- Requires `high Bandwidth`  
- Should be preferred for `long & steady` communication  
- it requires `Authentication`  

    ![image](https://user-images.githubusercontent.com/26399543/142746367-3efc8bf3-5edb-46f2-b69f-6c2564c5e6e2.png)

**Reference:**  
1. https://www.researchgate.net/figure/Connectionless-versus-connection-oriented-IP-packet-transmission-a-connectionless_fig1_335207402  
2. geeks-for-geeks  
