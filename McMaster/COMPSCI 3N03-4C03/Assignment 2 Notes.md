# Question 1

The sliding window protocol uses sequence numbers to keep track of the order in which frames are sent and received, and to detect and recover from lost or corrupted frames. The number of bits needed for the sequence number depends on the size of the sliding window, which in turn depends on the round trip time (RTT) and the maximum transmission rate (in bits per second) of the network.

To calculate the sliding window size, we first need to determine the maximum number of unacknowledged frames that can be in transit at any given time, which is given by:

`window_size = (transmission_rate * RTT) / frame_size`

where transmission_rate is the maximum transmission rate of the network in bits per second, RTT is the round trip time in seconds, and frame_size is the size of each frame in bytes.

In this case, we have:

```
transmission_rate = 10Mbps = 10,000,000 bps
RTT = 0.5 sec
frame_size = 20KB = 20,000 bytes
```

Plugging these values into the formula, we get:

`window_size = (10,000,000 * 0.5) / 20,000 = 25

So the maximum number of unacknowledged frames that can be in transit at any given time is 25. To accommodate this, we need a sequence number that can represent at least 25 different values. Since the sequence number is used to uniquely identify each frame, we require the sequence number to wrap around after it reaches its maximum value. Therefore, we require a sequence number that can wrap around at least 25 times.

The minimum number of bits required for this sequence number is given by:

$$

bits = ceil(log2(25 * 2)) = ceil(log2(50)) = 6

$$

So we require at least 6 bits for the sequence number to support a sliding window protocol with a window size of 25 frames on a 10Mbps network with a round trip latency of 0.5 second and 20 KB frame size.

# Question 2

The following statement is true about the routing algorithms:

-   If the cost on all the edges are the same, the shortest path from a source node to all other nodes computed by Dijkstra's algorithm is the breath first tree rooted at the source.

Explanation:

Dijkstra's algorithm is a shortest path algorithm used in network routing protocols to calculate the shortest path from a source node to all other nodes in a network. If the cost on all the edges are the same, then Dijkstra's algorithm will generate a breadth-first tree rooted at the source, where each node in the tree is the same distance from the source.

The other statements are false:

-   Distance vector routing (DVR) requires more bandwidth, whereas link state routing (LSR) requires less bandwidth. This statement is false. In fact, the opposite is true. Distance vector routing requires less bandwidth because routers only need to exchange their routing tables with their immediate neighbors, while link state routing requires more bandwidth because routers exchange more detailed information about the network topology.
-   Count to infinity problem is present in both DVR and LSR. This statement is false. The count-to-infinity problem is only present in distance vector routing protocols, not in link state routing protocols. In distance vector routing, a router can incorrectly believe that it has found a shorter path to a destination node and continue to broadcast this information to its neighbors, causing a routing loop.
-   Routing tables of a router keeps track of distributed IP addresses to network devices. This statement is false. Routing tables of a router keep track of network addresses and the next hop to reach that network, not individual IP addresses of devices.

# Question 3




# Question 4

In a sliding window protocol, the sender can transmit multiple frames at once without waiting for the acknowledgment of the previous frames. The receiver maintains a window of the frames it expects to receive next.

In this case, we have a sliding window protocol with a window size of 10, meaning that the receiver is expecting frames with sequence numbers 21 through 30. The receiver can receive any frame within this window and acknowledge it.

Out of the options given, the only impossible frame to arrive is 10. This is because the receiver is currently expecting frames with sequence numbers 21 through 30, and any frame with a sequence number less than 21 has already been acknowledged and is no longer expected.

Frames 15, 20, 25, and 30 are all within the receiver's current window and can be received and acknowledged. However, frame 10 is not within the current window and has already been acknowledged, so it is impossible for it to arrive again.

# Question 5

We can see that host A is connected to bridge B1, which is connected to bridge B2. Bridge B2 is then connected to bridge B3, which is connected to host C. Additionally, bridge B2 is also connected to bridge B4, which is connected to host D.

Since the forwarding tables for the bridges are initially empty, the bridges will use a flooding mechanism to forward packets. This means that when a bridge receives a packet, it will forward the packet out of all its ports, except for the port that the packet was received on.

In this case, if host A wants to send a packet to host C, the packet will be sent to bridge B1, which will flood the packet out of all its ports except for the port that the packet was received on (i.e., the port connected to host A). This means that the packet will be forwarded to bridge B2 and bridge B4.

Bridge B2 will receive the packet on two of its ports (one from B1 and the other from B4), and it will flood the packet out of all its ports except for the ports that the packet was received on. This means that the packet will be forwarded to bridge B3 and bridge B4.

Finally, bridge B3 will receive the packet and forward it out of the port connected to host C.

Therefore, the packet will be delivered from host A to host C through the following path:

`A -> B1 -> B2 -> B4 -> B2 -> B3 -> C`

Similarly, if host A wants to send a packet to host D, the packet will be sent to bridge B1, which will flood the packet out of all its ports except for the port that the packet was received on (i.e., the port connected to host A). This means that the packet will be forwarded to bridge B2 and bridge B4.

Bridge B2 will receive the packet on two of its ports (one from B1 and the other from B4), and it will forward the packet out of the port connected to bridge B4.

Bridge B4 will receive the packet and forward it out of the port connected to host D.

Therefore, the packet will be delivered from host A to host D through the following path:

`A -> B1 -> B2 -> B4 -> D`

(a)

Bridge B4 will also forward the message from host A to host C because it is connected to bridge B2, which is on the path between host A and host C.

When host A sends a message to host C, the message will be initially received by bridge B1. Since bridge B1 does not know the MAC address of host C, it will flood the message out of all its ports except for the port that the message was received on.

The message will then be received by bridge B2 on two of its ports (one from B1 and the other from B4). Bridge B2 will flood the message out of all its ports except for the ports that the message was received on.

The message will also be received by bridge B4 on one of its ports (from B2). Bridge B4 will flood the message out of all its ports except for the port that the message was received on.

Finally, the message will be received by bridge B3 and forwarded out of the port connected to host C.

Therefore, bridges B1, B2, B4, and B3 will forward the message from host A to host C. The path taken by the message is as follows:

`A -> B1 (flood) -> B2 (flood) -> B4 (flood) -> B2 -> B3 -> C`

(b)

You are correct, if host C sends a message to host D, all the bridges in the network will forward the message.

When host C sends a message to host D, the message will be initially received by bridge B3. Since bridge B3 does not know the MAC address of host D, it will flood the message out of all its ports except for the port that the message was received on.

The message will then be received by bridge B2 on one of its ports (from B3) and bridge B4 on another port (from host D). Both bridges B2 and B4 will flood the message out of all their ports except for the ports that the message was received on.

Finally, the message will be received by bridge B2 on one of its ports (from B4) and forwarded out of the port connected to bridge B1. Bridge B1 will then forward the message out of the port connected to host D.

Therefore, all the bridges in the network (B1, B2, B3, and B4) will forward the message from host C to host D. The path taken by the message is as follows:

`C -> B3 (flood) -> B2 (flood) -> B4 (flood) -> B2 -> B1 -> D`

(c)

When host A sends a message to host C, the message will be forwarded by bridges B1, B2, and B3.

The forwarding tables in the bridges will be updated as follows:

-   Bridge B1 will learn that the MAC address of host A is on port 1.
-   Bridge B2 will learn that the MAC addresses of host A and B1 are on port 2 and that the MAC address of host C is on port 3.
-   Bridge B3 will learn that the MAC addresses of host B2 and C are on port 2 and 3.

When host A sends a message to host C, the message will be initially received by bridge B1. Since bridge B1 does not know the MAC address of host C, it will flood the message out of all its ports except for the port that the message was received on.

The message will then be received by bridge B2 on two of its ports (one from B1 and the other from B4). Bridge B2 will forward the message out of the port connected to bridge B3.

Finally, the message will be received by bridge B3 and forwarded out of the port connected to host C.

Therefore, bridges B1, B2, and B3 will forward the message from host A to host C. The path taken by the message is as follows:

`A -> B1 (flood) -> B2 -> B3 -> C`
