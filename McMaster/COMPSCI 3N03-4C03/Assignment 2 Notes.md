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



Question 5

