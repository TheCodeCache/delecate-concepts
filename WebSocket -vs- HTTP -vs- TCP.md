# WebSocket
- It is an `Application Layer` protocol  
- It is `Bi-directional` communication.  
- It is like a `full-duplex` channel comm.  
- The connection is kept alive until terminated by client or by server  
- WebSocket uses `long lived persistent connection`  
- It is `stateful`, Obv. when we've a long lived persistent connection, then we can maintain states of information,  
  thus could do the computation on the data seen so far on the connection.  
- URL scheme: `ws://` or `wss://` (secured version)  
- It supports only `TCP` as of now under the hood for reliable data transfer over the network  
- It is mainly used by `real-time` application (trading app, like CoinDCX-bitcoins, Gaming app, etc.)  
- It is `faster` than HTTP  

    ![image](https://user-images.githubusercontent.com/26399543/142745671-9d1b172e-cd61-4697-95ff-d40e30d45043.png)


# HTTP
- It is an `Application Layer` protocol  
- It is `Uni-directional` communication.  
- - It is like a `half-duplex` channel comm.  
- The connection is immediately terminated with each http request/response  
- HTTP uses `short lived transient connection`  
- It is `stateless`, Obv. with every http request (be it client or server), it establishes a brand new connection,  
  thus has no idea about the information in the previous request or connection   
- URL scheme: `http://` or `https://` (secured version)  
- It supports `TCP`  and other N/W layer protocol that provides reliable data transfer over the network  
- It is mainly used by simple `RestFul` applications  
- It is `slower` than WebSocket  

    ![image](https://user-images.githubusercontent.com/26399543/142745703-a1e16724-f035-4af5-ace6-82522766be86.png)


# TCP
- It is a `Network Layer` protocol  
- It is `connection oriented` protocol, that means for to transfer a data or a n/w packet,  
  it first establishes the connection b/w client and server  
- Most of the Application Layer protocol such as `WebSocket` or `HTTP` uses TCP under the hood,  
  in order for reliable data transfer over the network or internet  
- It uses `internet protocol` i.e. `IP` under the hood, hence sometimes it is also called as `TCP/IP` protocol  

**Reference:**  
1. https://www.geeksforgeeks.org/what-is-web-socket-and-how-it-is-different-from-the-http/  


