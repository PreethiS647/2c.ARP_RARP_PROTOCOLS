# 2c.SIMULATING ARP /RARP PROTOCOLS
## AIM
To write a python program for simulating ARP protocols using TCP.
## ALGORITHM:
## Client:
1. Start the program
2. Using socket connection is established between client and server.
3. Get the IP address to be converted into MAC address.
4. Send this IP address to server.
5. Server returns the MAC address to client.
## Server:
1. Start the program
2. Accept the socket which is created by the client.
3. Server maintains the table in which IP and corresponding MAC addresses are
stored.
4. Read the IP address which is send by the client.
5. Map the IP address with its MAC address and return the MAC address to client.
P
## PROGRAM - ARP
## CLIENT - ARP
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"165.165.80.80":"6A:08:AA:C2","165.165.79.1":"8A:BC:E3:FA"}; while True:
ip=c.recv(1024).decode()
try:
c.send(address[ip].encode())
except KeyError:
c.send("Not Found".encode())
```
## SERVER - ARP
```
import socket
s = socket.socket()
s.connect(('localhost',8000))
while True:
ip = input("Enter logical address: ")
s.send(ip.encode())
print("MAC Address",s.recv(1024).decode())

```
## OUPUT - ARP
## CLIENT-ARP
![Screenshot 2024-05-07 093746](https://github.com/PreethiS647/2c.ARP_RARP_PROTOCOLS/assets/147313372/d8371570-a801-459b-9500-5977c94fd6cf)

## SERVER-ARP
![Screenshot 2024-05-07 093703](https://github.com/PreethiS647/2c.ARP_RARP_PROTOCOLS/assets/147313372/a25934ad-1cf1-4b0c-b35f-2b728a2306f3)


## PROGRAM - RARP
## CLIENT-RARP
```
import socket
s = socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr = s.accept()
address = {"6A:08:AA:C2":"165.165.80.1","8A:BC:E3:FA":"165.165.79.1"}
while True:
ip = c.recv(1024).decode()
try:
c.send(address[ip].encode())
except KeyError:
c.send("Not Found".encode())
```
## SERVER-RARP
```
import socket
s = socket.socket()
s.connect(('localhost',8000))
while True:
ip = input("Enter MAC address: ")
s.send(ip.encode())
print("Logical Address",s.recv(1024).decode())


```
## OUPUT -RARP
## CLIENT-RARP

![Screenshot 2024-05-07 094356](https://github.com/PreethiS647/2c.ARP_RARP_PROTOCOLS/assets/147313372/d88fd283-2bb6-4b60-a6da-4958a7a6d94c)

## SERVER=RARP

![Screenshot 2024-05-07 094443](https://github.com/PreethiS647/2c.ARP_RARP_PROTOCOLS/assets/147313372/e7c51d5b-870d-411a-bae4-15dfa45a27af)

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
