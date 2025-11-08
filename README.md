# 3b.CREATION FOR CHAT USING TCP SOCKETS
## AIM
To write a python program for creating Chat using TCP Sockets Links.
## ALGORITHM:
1. Import the necessary modules in python
2. Create a socket connection to using the socket module.
3. Send message to the client and receive the message from the client using the Socket module in
 server
4. Send and receive the message using the send function in socket.
## PROGRAM

Server
```
import socket

s = socket.socket()
s.bind(('localhost', 8000))
s.listen(5)
print("Server listening on port 8000...")
c, addr = s.accept()
print(f"Connection from {addr}")

while True:
    try:
        ClientMessage = c.recv(1024).decode()
        if not ClientMessage:
            break
        print("Client >", ClientMessage)
        msg = input("Server > ")
        c.send(msg.encode())
    except (ConnectionResetError, ConnectionAbortedError):
        print("Client disconnected")
        break
    except KeyboardInterrupt:
        print("\nServer shutting down...")
        break

c.close()
s.close()
```

Client
```
import socket

s = socket.socket()
try:
    s.connect(('localhost', 8000))
    print("Connected to server")
    
    while True:
        try:
            msg = input("Client > ")
            s.send(msg.encode())
            response = s.recv(1024).decode()
            print("Server >", response)
        except KeyboardInterrupt:
            print("\nDisconnecting...")
            break
        except ConnectionResetError:
            print("Server disconnected")
            break
except ConnectionRefusedError:
    print("Could not connect to server")

s.close()
```

## OUPUT

Server

<img width="528" height="419" alt="Screenshot 2025-11-06 101551" src="https://github.com/user-attachments/assets/d663c113-f23b-41e1-bc48-c18131e6e2e2" />

Client


<img width="566" height="420" alt="Screenshot 2025-11-06 101637" src="https://github.com/user-attachments/assets/66d9a96e-7535-4cdf-bc0d-9a6debe514b4" />


## RESULT
Thus, the python program for creating Chat using TCP Sockets Links was successfully 
created and executed.
