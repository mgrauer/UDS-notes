# Communication

Networking stack composed of multiple layers, each building on the next.

* Link layer - local network links with interfaces to hardware
* Internet Layer (IP) - routes from one machine to another
* Transport Layer (TCP/UDP) - routes from one process to another
* TCP provides reliable channels on top of IP
* Application layer - e.g. HTTPS/DNS - communicates in the semantics of an application

# Chapter 2 Reliable Links

We need a way to address nodes and route packets.

* IP provides addressing
* BGP (Border Gateway Protocal) maintains routing tables

## TCP (Transport Layer Protocal)

Builds a reliable and stable channel with a bytestream abstraction on top of an unreliable channel that can only send discrete packets. TCP provides for retransmission, in order delivery, and error correction.

* TCP is stateful, there is a connection lifecycle of a socket
* 3 way handshake: syn, synack, ack; to build the connection
* Flow control -- a backoff mechanism (back pressure) to protect the receiver from being overwhelmed, rate limiting at the connection level
  * Receiver communicates size of receive buffer when it acknolwedges receipt of a segment
  * Sender will avoid sending more data than can fit in receive buffer
* Congestion control -- protects the network from being overwhelmed
  * Slow start and ramp up to implement this
  * bandwidth of a connection = window size / round trip time (RTT); size of congestion window is the max bytes that can be sent without receiver acknowledgement
  * shorter the round trip time (and the closer the connection) the higher the bandwidth
  * bandwidth is a function of latency
* UDP (User Datagram Protocol) is stateless (connectionless), sends discrete packets
  * no reliability or flow or congestion control, no sequencing
  * used to bootstrap custom protocols or for e.g. game updates or video frames, where retranmission isn't useful
