# TCP Analysis - Wireshark Trace File

This document contains answers and explanations for questions based on the trace file `tcp-ethereal-trace-1`, which can be found in [Wireshark Traces](http://gaia.cs.umass.edu/wireshark-labs/wireshark-traces.zip).

---

### **Analyze the TCP segments:**

### **1. What is the IP address and TCP port number used by your client computer (source) to transfer the file to `gaia.cs.umass.edu`?** (10%) 

![Figure 1](assets/no1.png)

---

### **Answer**

**Based on the figure above:**
- **Client's (Source) IP Address**: `192.168.1.102`
- **TCP Port Number**: `1161`

### **Simplified Explanation**

#### **1. IP Address of the Client**  
The IP address serves as the unique "home address" for the client computer within the network. In this case, the client computer's IP address is:  
`192.168.1.102`

####  **2. TCP Port Number**  
The TCP port number functions as a "door" on the client computer for network communication. It is used to identify the specific application or process handling the connection. For this transfer, the client uses:  
`1161`

####  **Summary**
- **Client IP Address**: `192.168.1.102`
- **TCP Port**: `1161`

---

### **2. What does `gaia.cs.umass.edu` use the IP address and port number to receive the file?**  
(Attach the screenshot of your Wireshark's display) (10%)

![Figure 2](assets/no2.png)

---

### **Answer**

**From the figure above:**
- **Server's (gaia.cs.umass.edu) IP Address**: `128.119.245.12`
- **TCP Port Number**: `80`

### **Simplified Explanation**

#### **1. IP Address of the Server (gaia.cs.umass.edu)**  
The server is identified by the IP address `128.119.245.12`, which acts as its unique "home address" on the internet.  

#### **2. TCP Port Number of the Server**  
The TCP port number `80` is used by the server to communicate over the HTTP protocol.  
- Port `80` is the standard port for serving web pages and handling HTTP requests.  

#### **Summary**
- **Server IP Address**: `128.119.245.12`
- **TCP Port**: `80`

---

### **3. What is the sequence number of the TCP SYN segment that is used to initiate the TCP connection between the client computer and `gaia.cs.umass.edu`? What is it in the segment that identifies the segment as a SYN segment?**  
(Attach the screenshot of your Wireshark's display) (10%)

![Figure 3](assets/no3.png)

---

### **Answer**

**From the figure above:**
- **Sequence Number of the TCP SYN Segment**: `0`
- **Identifying the SYN Segment**: The SYN flag in the TCP header is enabled (set to `1`).

### **Simplified Explanation**

#### **1. Sequence Number**  
The sequence number in TCP is a field in the header used to track data packets sent during a connection.  
- A SYN segment typically has a sequence number of `0` because it is the initial packet sent to establish the connection.  
- This value acts as the starting point for tracking subsequent data packets exchanged between the client and the server.

#### **2. Purpose of the SYN Segment**  
A SYN segment is the first step in the three-way handshake, a mechanism used by TCP to establish a reliable connection.  
- The client sends a SYN segment to the server, signaling its intent to start communication.  

#### **3. Identifying the SYN Segment**  
The TCP header includes a **Flags** section where various control bits indicate the purpose of the segment:  
- When the **SYN flag** is set to `1`, it explicitly identifies the segment as a SYN segment.  
- In the provided figure, the SYN flag is highlighted as active (`1`), confirming this is the connection initiation segment.  

#### **Summary**
- **Sequence Number**: `0`
- **SYN Flag**: Enabled (`1`)
- **Purpose**: To initiate a TCP connection as part of the three-way handshake.

---

### **4. What is the sequence number of the SYN-ACK segment sent by `gaia.cs.umass.edu` to the client computer in reply to the SYN? What is the value of the ACKnowledgement field in the SYN-ACK segment? How did `gaia.cs.umass.edu` determine that value? What is it in the segment that identifies the segment as a SYN-ACK segment?**  
(Attach the screenshot of your Wireshark's display) (10%)

![Figure 4](assets/no4.png)

---

### **Answer**

**From the figure above:**
- **Sequence Number of the SYN-ACK Segment**: `0`
- **Acknowledgment Field in the SYN-ACK Segment**: `1`
- **Identifying the SYN-ACK Segment**: Both the SYN flag and the ACK flag in the TCP header are set to `1`.

---

### **Detailed Explanation**

#### **1. Sequence Number of SYN-ACK Segment**  
The sequence number of the SYN-ACK segment is `0`. This is typical because the server uses its own initial sequence number to begin communication. It signifies that this is the server's first packet in the handshake process.  

#### **2. Acknowledgment Field in SYN-ACK Segment**  
The acknowledgment (ACK) field in the TCP header is used to acknowledge the receipt of data:  
- In the SYN-ACK segment, the server sets the acknowledgment field to `1` by taking the sequence number of the SYN segment received from the client (which is `0`) and adding `1` to it.  
- This confirms that the server has received the SYN segment from the client.  

#### **3. Purpose of SYN-ACK Segment**  
The SYN-ACK segment serves two critical purposes in the three-way handshake process of TCP:  
1. **Acknowledges** the receipt of the SYN segment from the client (via the ACK field).  
2. **Signals** the server's intent to establish the connection by setting the SYN flag.  

#### **4. Identifying the SYN-ACK Segment**  
A SYN-ACK segment is recognized by inspecting the Flags field in the TCP header:  
- Both the **SYN flag** and the **ACK flag** are set to `1`.  
- This distinguishes the SYN-ACK segment from other types of segments.

---

### **Conclusion**  
The SYN-ACK segment, with:  
- **Sequence Number**: `0`  
- **Acknowledgment Field**: `1`  
is crucial for confirming the initiation of a connection between the client and the server. By setting both the SYN and ACK flags, the server signals its readiness to establish a connection and proceed with the handshake.  

---

### **5. What is the sequence number of the TCP segment containing the HTTP POST command?**  
Note: To find the POST command, inspect the packet content field at the bottom of the Wireshark window and look for a segment with "POST" in its DATA field.  
(Attach the screenshot of your Wireshark's display) (15%)

![Figure 5](assets/no5.png)

---

### **Answer**

**From the figure above:**  
- **Segment No.**: `4`  
- **Sequence Number of the Segment Containing the POST Command**: `1`

---

### **Detailed Explanation**

#### **1. Understanding the HTTP POST Command**  
The HTTP POST command is used by a client to send data to a server, typically as part of an HTTP request.  
- This data can include form inputs, file uploads, or other client-generated content.  
- In Wireshark, the POST command is located in the data payload of a TCP segment because HTTP operates over the TCP protocol.  

#### **2. Locating the POST Command in Wireshark**  
- Use Wireshark to analyze network traffic and locate the TCP segment containing the POST command.  
- Navigate to the packet content field at the bottom of the Wireshark interface.  
- Look within the **DATA field** for the keyword **"POST"**, which indicates that the segment contains the HTTP POST command.  

#### **3. Sequence Number in TCP**  
The sequence number in the TCP header identifies the order of bytes in the data stream:  
- For the segment containing the POST command, the sequence number represents the starting byte position of this segment in the TCP connection.  

#### **4. Sequence Number in This Example**  
According to the provided figure:  
- The fourth segment (**Segment No. 4**) contains the HTTP POST command.  
- The **Sequence Number** for this segment is `1`.  
- This means it starts transmitting data from the second byte in the TCP stream (assuming the initial sequence number is `0`).  

---

### **Conclusion**  
The sequence number of the TCP segment containing the HTTP POST command is critical for understanding data flow within the connection.  
- **Segment Containing POST Command**: No. `4`  
- **Sequence Number**: `1`  

---

### **6. Consider the TCP segment containing the HTTP POST as the first segment in the TCP connection.**  
What are the sequence numbers of the first six TCP connection segments (including the HTTP POST segment)? At what time was each segment sent? When was the ACK for each segment received? Given the difference between when each TCP segment was sent and when its acknowledgement was received, what is the RTT value for each of the six segments? What is the EstimatedRTT value (see page 237 in the textbook) after the receipt of each ACK? Assume that the value of the EstimatedRTT is equal to the measured RTT for the first segment, and then is computed using the EstimatedRTT equation on page 237 for all subsequent segments.  
Note: Wireshark has a nice feature that allows you to plot the RTT for each of the TCP segments sent. Select a TCP segment in the “listing of captured packets” window that is being sent from the client to the gaia.cs.umass.edu server. Then select: Statistics -> TCP Stream Graph -> Round Trip Time Graph.

![Figure 6a](assets/no6.png)  
![Figure 6b](assets/no6b.png)  

---

### **Answer**

The HTTP POST segment is treated as the first segment in this trace. Segments 1 through 6 correspond to packets numbered 4, 5, 7, 8, 10, and 11 in the captured data. The ACKs for these segments are found in packets numbered 6, 9, 12, 14, 15, and 16, respectively.

The sequence numbers for each segment are as follows:
- **Segment 1**: Sequence number `1`
- **Segment 2**: Sequence number `566`
- **Segment 3**: Sequence number `2026`
- **Segment 4**: Sequence number `3486`
- **Segment 5**: Sequence number `4946`
- **Segment 6**: Sequence number `6406`

| Segment     | Sent Time   | ACK Received Time | RTT (Seconds) |
|-------------|-------------|-------------------|---------------|
| **Segment 1** | 0.026477    | 0.053937          | 0.02746       |
| **Segment 2** | 0.041737    | 0.077294          | 0.035557      |
| **Segment 3** | 0.054026    | 0.124085          | 0.070059      |
| **Segment 4** | 0.054690    | 0.169118          | 0.11443       |
| **Segment 5** | 0.077405    | 0.217299          | 0.13989       |
| **Segment 6** | 0.078157    | 0.267802          | 0.18964       |

---

### **EstimatedRTT Calculation**

The EstimatedRTT is calculated using the formula:  
**EstimatedRTT = 0.875 * EstimatedRTT + 0.125 * SampleRTT**

#### **EstimatedRTT after the receipt of the ACK of segment 1**:  
- **EstimatedRTT** = RTT for Segment 1 = **0.02746**

#### **EstimatedRTT after the receipt of the ACK of segment 2**:  
- **EstimatedRTT** = 0.875 * 0.02746 + 0.125 * 0.035557 = **0.0285**

#### **EstimatedRTT after the receipt of the ACK of segment 3**:  
- **EstimatedRTT** = 0.875 * 0.0285 + 0.125 * 0.070059 = **0.0337**

#### **EstimatedRTT after the receipt of the ACK of segment 4**:  
- **EstimatedRTT** = 0.875 * 0.0337 + 0.125 * 0.11443 = **0.0438**

#### **EstimatedRTT after the receipt of the ACK of segment 5**:  
- **EstimatedRTT** = 0.875 * 0.0438 + 0.125 * 0.13989 = **0.05585**

#### **EstimatedRTT after the receipt of the ACK of segment 6**:  
- **EstimatedRTT** = 0.875 * 0.0558 + 0.125 * 0.18964 = **0.0725**

### **Round Trip Time Graph**
![Figure 6a](assets/no6c.png)  
![Figure 6b](assets/no6d.png) 

---

### **7. What is the length of each of the first six TCP segments?**  
(Attach the screenshot of your Wireshark's display) (15%)

![Figure 7](assets/no7.png)

---

### **Answer**

The first TCP segment, which includes the HTTP POST command, has a size of 565 bytes. This segment is smaller than the subsequent ones because, in addition to carrying application data, it also includes the TCP header necessary for maintaining communication. Following this, there are five additional TCP segments, each 1460 bytes in length. This size matches the Maximum Segment Size (MSS) agreed upon during the TCP connection setup. The MSS ensures that the segment size stays within the network's capacity, preventing fragmentation and improving the efficiency of data delivery.

---

### **Simplified Explanation**

#### **Why the First Segment is Smaller:**  
- The first TCP segment carries the HTTP POST command, which is relatively short (565 bytes).
- It is smaller because it not only carries the application data but also includes the TCP header, which manages communication between devices.

#### **Length of the Following Segments:**  
- The next five segments are all 1460 bytes long. This is the Maximum Segment Size (MSS) agreed upon when the TCP connection is established.

#### **What is MSS and Why it Matters:**  
- MSS is a limit on how much data can be sent in a single TCP segment.
- It helps ensure that the segments are small enough to be handled by the network without needing to split them into smaller pieces (fragmentation).
- Avoiding fragmentation makes data delivery faster and more efficient, improving network performance.

---

### **In Summary**
- The first segment is smaller because it contains extra information (TCP header) alongside the application data.
- The other segments are larger but capped at the MSS limit, ensuring smooth transmission over the network.

