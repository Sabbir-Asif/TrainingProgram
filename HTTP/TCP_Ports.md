## TCP (Transmission Control Protocol)  
TCP is a transport-layer protocol, responsible for establish a connection between two machines. TCP consists of 2 protocols: TCP and UDP (User Datagram Package).  TCP is reliable, each packet has a sequence number, and an acknowledgement is expected.  A packet will be re-transmitted if it is not received by the receiver.  Packet delivery is guaranteed in TCP.  UDP does not guarantee packet delivery, and is therefore not reliable.  However, UDP has less network overhead and can be used for applications such as video and audio streaming, where reliability is not critical.  

### TCP multiplexes applications within an IP machine.
For each IP machine, TCP supports (multiplexes) up to <b>65536</b> ports (or sockets), from port number 0 to 65535.

#### Port 0 to 1023 are pre-assigned to popular protocols
- HTTP at 80
- FTP at 21
- Telnet at 23
- SMTP at 25
- NNTP at 119
- DNS at 23

#### Port 1024 and above are available to the users.