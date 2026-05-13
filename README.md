# 2a_Stop_and_Wait_Protocol
## AIM 
To write a python program to perform stop and wait protocol
## ALGORITHM
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
server:
~~~
import socket


s = socket.socket()


s.bind(('localhost', 8000))

s.listen(5)

print("Server waiting for connection...")


c, addr = s.accept()
print("Connected with:", addr)

while True:
   
    i = input("Enter a data: ")
    c.send(i.encode())

    
    ack = c.recv(1024).decode()

    if ack:
        print("Client says:", ack)
        continue
    else:
        c.close()
        break
~~~
client:
~~~
import socket

s = socket.socket()
s.connect(('localhost', 8000))

while True:
    print(s.recv(1024).decode())
    s.send("Acknowledgement Received".encode())
~~~
## OUTPUT
server: 

<img width="1920" height="245" alt="Screenshot (241)" src="https://github.com/user-attachments/assets/7e7bda52-bab4-4db3-bf89-b71fe7c929a8" />

client:

<img width="846" height="219" alt="Screenshot (242)" src="https://github.com/user-attachments/assets/96f325f8-1cd0-4f8b-b8e1-084b7279b6c6" />

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.
