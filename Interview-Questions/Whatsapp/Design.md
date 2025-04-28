**Whatsapp Design**

1. Client sends an HTTP/1.1 upgrade request to the server, asking it to upgrade the connection to a bi-directional web socket protocol.
2. If the server supports it, it responds with an "HTTP 101 Switching Protocols" response.
3. After this handshake, the connection switches from HTTP to a full duplex WebSocket connection
4. Once the WebSocket is established, communication happens through messages (commands)
5. Connection is established with a L4 Elastic load balancer (transport layer LB) since it is very lightweight and efficient for just forwarding raw TCP traffic to backend servers.
6. First, chat 
