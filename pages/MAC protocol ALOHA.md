- Slotted ALOHA
	- Assumptions
		- Frames share a same length.
		- Time partitioned into equal size slots.
		- Nodes start to transmit only at slot beginning.
		- **Nodes are synchronized.**
		- If 2 or more nodes transmit in slot, all nodes detect collision.
	- Protocol
		- When a node has a new frame to send, it sends the frame right away.
		- If no collision, the node sends next frame (if has) in next slot.
		- If collided, in each following slot, the node has a probability of $p$ to resend that frame.
	- Efficiency
		- $\lim_{n\to +\infty} np^*(1-p^*)^{n-1}=1/e=0.37$
		- where $p^*$ is the optimal $p$ according to $n$.
- Pure ALOHA
	- Do not slot time or synchronize between nodes.
	- On collision: wait for a random amount of time.
	- Efficiency: 0.18 (half of the slotted one)
	-