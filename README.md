# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
SERVER
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
size=int(input("Enter number of frames to send : "))
l=list(range(size))
s=int(input("Enter Window Size : "))
st=0
i=0
while True:
 while(i<len(l)):
 st+=s
 c.send(str(l[i:st]).encode())
 ack=c.recv(1024).decode()
 if ack:
 print(ack)
 i+=s
```
CLIENT
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True: 
 print(s.recv(1024).decode())
 s.send("acknowledgement recived from the server".encode())
```
## OUPUT
![326901028-303f3c9a-d7b9-4379-9b01-be842283c966](https://github.com/VerginJenifer/2b_SLIDING_WINDOW_PROTOCOL/assets/136251012/10d8b8a1-bd3a-45da-bc47-3ee3c493a348)
![326901086-71d635d6-19ec-454f-b7fb-a8133514b92f](https://github.com/VerginJenifer/2b_SLIDING_WINDOW_PROTOCOL/assets/136251012/65024bc4-7a64-4eca-8498-a398b48748d9)

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
