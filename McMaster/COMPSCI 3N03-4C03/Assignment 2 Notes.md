### Question 1

To determine the minimum number of bits required for the sequence number in a sliding window protocol, we need to consider the maximum number of frames that can be in transit at any given time.

First, we need to calculate the maximum number of frames that can be in transit using the given bandwidth and round trip latency.

Bandwidth-delay product = bandwidth x round trip latency = 10Mbps x 0.5s = 5,000,000 bits

This is the maximum amount of data that can be "in flight" at any given time.

Next, we need to determine the maximum number of frames that can be in transit at any given time, given that each frame carries 20KB (20,480 bytes) of data.

Maximum number of frames in transit = Bandwidth-delay product / Frame size = 5,000,000 bits / 20,480 bytes = 244.14 frames

Since the number of frames must be a whole number, we can round up to 245 frames.

To represent 245 unique frame numbers, we need at least 8 bits (2^8 = 256). Therefore, the minimum number of bits required for the sequence number is 8.

### Question 2

The following statement is true about the routing algorithms:

-   If the cost on all the edges are the same, the shortest path from a source node to all other nodes computed by Dijkstra's algorithm is the breath first tree rooted at the source.

Explanation:

Dijkstra's algorithm is a shortest path algorithm used in network routing protocols to calculate the shortest path from a source node to all other nodes in a network. If the cost on all the edges are the same, then Dijkstra's algorithm will generate a breadth-first tree rooted at the source, where each node in the tree is the same distance from the source.

The other statements are false:

-   Distance vector routing (DVR) requires more bandwidth, whereas link state routing (LSR) requires less bandwidth. This statement is false. In fact, the opposite is true. Distance vector routing requires less bandwidth because routers only need to exchange their routing tables with their immediate neighbors, while link state routing requires more bandwidth because routers exchange more detailed information about the network topology.
    
-   Count to infinity problem is present in both DVR and LSR. This statement is false. The count-to-infinity problem is only present in distance vector routing protocols, not in link state routing protocols. In distance vector routing, a router can incorrectly believe that it has found a shorter path to a destination node and continue to broadcast this information to its neighbors, causing a routing loop.
    
-   Routing tables of a router keeps track of distributed IP addresses to network devices. This statement is false. Routing tables of a router keep track of network addresses and the next hop to reach that network, not individual IP addresses of devices.

Question 3


Question 4

In a sliding window protocol with RWS=SWS=10, if the next frame expected is 21, the receiver is currently expecting frames 21 through 30, inclusive. Any frame with a sequence number less than 21 or greater than 30 would be impossible to arrive at the receiver.

Therefore, the following frames are impossible to arrive at the receiver:

-   Frames with sequence numbers 1 to 20
-   Frames with sequence numbers greater than 30

Note that the frame with sequence number 31 is the next frame after the current receive window, and it is possible for it to arrive at the receiver as long as frames 21 to 30 have already been received and acknowledged.

In a sliding window protocol with RWS=SWS=10, if the next frame expected is 21, then the receiver is expecting frames with sequence numbers 21, 22, 23, ..., 30.

Therefore, the following frame(s) are impossible to arrive to the receiver:

-   10, since it is too far behind the expected next frame.
-   15 and 20, since they have already been received by the receiver (assuming no duplicate frames).
-   30, since it is too far ahead of the expected next frame.

The only remaining frame from the given options is 25, which is within the receiver's window and could potentially be received.

Question 5

