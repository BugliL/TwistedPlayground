# TwistedPlayground
Notes about Twisted library and event driven developing in python3


## Basic concept
 * *Events* : something that occur and witch the program should react.
 * *Event handler* : program reaction to events
 * *Event loop* : waiting loop that invoke an event handler if an event occur
 * *Busy wait* : situation where the program is active but waiting for an event
 * *Multiplexing* : bring many separated event input into one
 * *Demultiplexing* : separate inputs from a unique stream

### Select Multiplexer
A sample code for a client and a server is
```python
import socket

# Create a socket for internet and TCP socket
listener = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
listener.bind( ('127.0.0.1', 0) )
listener.listen()

client = socket.create_connect(listener.getsockname())
server, _ = listener.accept()
```

Reading and writing example
```python
data = b'binary data to send'

# client sending to server
client.sendall(data)
recived_data = server.recv(1024)

# server sending to client
server.sendall(data)
recived_data = client.recv(1024)
```
