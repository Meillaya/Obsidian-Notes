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

So the maximum number of unacknowledged frames that can be in transit at any given time is 25. To accommodate this, we need a sequence number that can represent at least 25 different values. Since the sequence number is used to uniquely identify each frame, we need the sequence number to wrap around after it reaches its maximum value. Therefore, we need a sequence number that can wrap around at least 25 times.

The minimum number of bits required for this sequence number is given by:

$$

bits = ceil(log2(25 * 2)) = ceil(log2(50)) = 6

$$

So we need at least 6 bits for the sequence number to support a sliding window protocol with a window size of 25 frames on a 10Mbps network with a round trip latency of 0.5 second and 20KB frame size.

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

