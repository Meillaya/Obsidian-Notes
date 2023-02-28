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


# Question 2

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

