# socket

## Server

```python
'''
server
keep-alive(/persistent) connections, short-lived connections, heartbeat packet
'''
import socket
import time

BUF_SIZE = 1024
host = 'localhost'  # Symbolic name meaning all available interfaces
port = 8083  # Arbitrary non-privileged port

server = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
server.bind((host, port))
server.listen(1)
client, address = server.accept()  # If server.listen(n) and n greater than 1, this will be...

while True:
    print(time.time())
    client.sendall('Hello Socket From Server\r\n'.encode())
    data = client.recv(BUF_SIZE)
    print data
    # client.close()  # keep-alive(/persistent) connections
```

## Client

```python
'''
client
keep-alive(/persistent) connections, short-lived connections, heartbeat packet
'''
import socket
import time

BUF_SIZE = 1024
host = 'localhost'  # The remote host
port = 8083  # The same port as used by the server

client = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
client.setsockopt(socket.SOL_SOCKET, socket.SO_KEEPALIVE, 1)  # keep-alive(/persistent) connections
client.connect((host, port))

while True:
    print(time.time())
    client.send('Hello Socket From Client\r\n'.encode())
    data = client.recv(BUF_SIZE)
    print data
    # If you want to check whether connection closed after a period of time
    # You can make it sleep a long time
    # time.sleep(1)
```

## References

[1] Docs@Python, [17.2. socket — Low-level networking interface](https://docs.python.org/2.7/library/socket.html)