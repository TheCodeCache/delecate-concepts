# Proxy Server:  
A `proxy server`, sometimes referred to as a `forward proxy`,  
is a server that routes traffic between client(s) and another system,  
usually external to the network.  
By doing so, it can regulate traffic according to preset policies, convert and mask client IP addresses, enforce security protocols, and block unknown traffic.  


# Forward Proxy: 
>`A forward proxy provides proxy services to a client or a group of clients on the internal network`  

**forward proxy servers provide `a single point of access and control`**.

Often, these clients belong to a common internal network like the one shown below.  
![image](https://user-images.githubusercontent.com/26399543/147322048-a1d8d16a-fcbf-4809-b2a4-a6e26812d474.png)


# Reverse proxy: 
A reverse proxy is a type of proxy server.  
>Unlike a traditional proxy server, which is used to protect clients,  
>`a reverse proxy is used to protect servers on the internal network.`  

A reverse proxy is a server that accepts a request from a client,  
forwards the request to another one of many other servers,  
and returns the results from the server that actually processed the request to the client as if the proxy server had processed the request itself.  
The client only communicates directly with the reverse proxy server and it does not know that some other server actually processed its request.  

**In other words:**  
A reverse proxy does the exact opposite of what a forward proxy does.  
While a forward proxy proxies on behalf of clients (or requesting hosts),  
a reverse proxy proxies on behalf of servers.  
A reverse proxy accepts requests from external clients on behalf of servers stationed behind it as shown below.  

![image](https://user-images.githubusercontent.com/26399543/147322197-24f463ae-69e4-4ab5-a34b-cff09e6df9a0.png)

**Just like forward proxy servers, reverse proxies also provide `a single point of access and control`**.

# Reverse proxy configuration: 
By routing client traffic through a reverse proxy, admins can `simplify security administration`  
They can configure backend servers to only accept traffic directly from the proxy and then configure the granular access control configurations on the proxy itself.  

For example, admins can configure the reverse proxy’s firewall `to whitelist or blacklist specific IP addresses`  

Using a reverse proxy can also allow administrators to `easily swap backend servers in and out without disrupting traffic`.  
Because clients interact directly with the proxy, they only need to know its host name and don't need to worry about changes to the backend network topology.  
An admin can configure a reverse proxy `to load-balance traffic`  
so that requests can be more evenly distributed to the backend servers and `improve overall performance`.  

```shell
server {
    listen 80;

    server_name github.com;

    location / {
        proxy_pass http://127.0.0.1:8080/;
    }
}
```
Through the above cofiguration, `we can direct outside client's request to the servers on our internal network running on un-conventional random ports`  
For ex: we can run our webserver on a radon port like 6774, which is not the default port of a web-server (usually 80), but using the above reverse proxy configuration,  
we can redirect trafiic from outside clients to a server running on 6774 port number.  

# Classic Example - 
**Forward Proxy**:  
When we want our client computers or users from our internal network to stop accessing websites like facebook.com or youtube.com or any entertaining or adult sites then we can use forward proxy to restrict their accesses.  
**Reverse Proxy**:  
When we want our internal servers to protect from unauthorized access from outside users/clients/server computers, then reverse proxy can help us in this case.  

**Reference:**  
1. https://www.jscape.com/blog/bid/87783/forward-proxy-vs-reverse-proxy
2. https://www.strongdm.com/blog/difference-between-proxy-and-reverse-proxy

