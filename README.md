# 2c.SIMULATING ARP /RARP PROTOCOLS
## AIM:
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

## PROGRAM - ARP
### Client program:
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"165.165.80.80":"6A:08:AA:C2","165.165.79.1":"8A:BC:E3:FA"};
while True:
    ip=c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("Not Found".encode())
```
### Server program:
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    ip=input("Enter logical Address : ")
    s.send(ip.encode())
    print("MAC Address",s.recv(1024).decode())
```
## OUPUT - ARP
### Client output:
![Screenshot 2024-03-07 191127](https://github.com/HEMAKESHG/2c.ARP_RARP_PROTOCOLS/assets/144870552/d379cc64-4bbe-4885-a458-71cfa26799ce)

### Server output:
![Screenshot 2024-03-07 191144](https://github.com/HEMAKESHG/2c.ARP_RARP_PROTOCOLS/assets/144870552/ebe97570-656f-42a8-8518-dc261b039ef2)

## PROGRAM - RARP
### Client program:
```
import socket
s=socket.socket()
s.bind(('localhost',9000))
s.listen(5)
c,addr=s.accept()
address={"6A:08:AA:C2":"192.168.1.100","8A:BC:E3:FA":"192.168.1.99"};
while True:
    ip=c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("Not Found".encode())
```
### Server program:
```
import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
    ip=input("Enter MAC Address : ")
    s.send(ip.encode())
    print("Logical Address",s.recv(1024).decode())
```
## OUTPUT -RARP
### Client output:
![Screenshot 2024-03-07 185331](https://github.com/HEMAKESHG/2c.ARP_RARP_PROTOCOLS/assets/144870552/8b8750ac-5ffd-4e5d-83cb-2c6766f40ee3)

### Server output:
![Screenshot 2024-03-07 185349](https://github.com/HEMAKESHG/2c.ARP_RARP_PROTOCOLS/assets/144870552/635bc36f-f75f-454f-815a-22360f679278)

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
