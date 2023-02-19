Question 1
Suppose you are designing a sliding window protocol for a 10Mbps with round trip latency of 0.5 second. Assuming that each frame carries 20KB of data, what is the minimum number of bits you need for the sequence number?

Question 2
Which of the following statement is true about the routing algorithms?

- Distance vector routing (DVR) requires more bandwidth whereas link state routing (LSR) requires less bandwidth.

- Count to infinity problem is present in both DVR as well as LSR.

- If the cost on all the edges are the same, the shortest path from a source node to all other nodes computed by Dijkstra's algorithm is the breath first tree rooted at the source.

- Routing tables of a router keeps track of distributed IP addresses to network devices

Question 3
Using the network given in the figure. Provide the virtual circuit tables for all the switches after each of the following connection is established. Assume that the sequence of connection is cumulative. Also assume that the VCI assignment always picks the lowest unused VCI on each link, starting with 0, and that a VCI is consumed for both directions of a virtual circuits.

1.  Host A connects to Host B
2.  Host D connects to Host E
3.  Host C connects to Host B
4.  Connection from Host D to E was removed
5.  Host A connects to F
![[McMaster/COMPSCI 3N03-4C03/q3.png]]
What's the destination of a packet sent on port 1 of switch 1 with output VCI=1?
- B
- C
- D
- E
- F

Question 4
In a sliding window protocol with RWS=SWS=10, a very large set of possible sequence numbers (assume no wrapping), and in-order packet arrivals. If the next frame expected is 21, which of the following frame(s) are impossible to arrive to the receiver. 

- 10

- 15

- 20

- 25

- 30

## Forwarding Table for Bridges

Question 5, 6, 7 are asked in sequence

## **Question 5** (0.34 points)


Consider the local area network (LAN) shown in the following figure. Assume that the forwarding tables for the bridges are initially empty.

![](https://avenue.cllmcmaster.ca/content/enforced/527485-COMPSCI_4C03_hew11_2231/PastedImage_cca0292c8415421bb5123b18ae81ebdd_image.png?_&d2lSessionVal=ORTzZAStUvaAuUPaFRIzxOGLA)

If A sends a message to C, which bridge(s) forward the message?

- **All the bridges B1, B2, B3, and B4 forward the message**

- B1, B2 and B3 forward the message.

## **Question 6** (0.33 points)

Then if C sends a message to D, which bridge(s) forward the message?

- **All the bridges B1, B2, B3, and B4 forward the message**

- B2, B3 and B4 forward the message.

## **Question 7** (0.33 points)

Next, if A sends a message to C, which bridge(s) forward the message?

- All the bridges B1, B2, B3, and B4 forward the message

- **B1, B2 and B3 forward the message.**