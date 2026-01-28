# Data Link Layer Protocols Implementation

**Course:** Telecommunications Systems
**Language:** Java  
**Context:** Network Simulator (`terminal.Simulator`)

## 📄 Project Description

This project consists of the implementation of various Data Link Layer protocols, ranging from simple theoretical approaches to robust sliding window mechanisms with flow control. The goal is to ensure reliable data transmission over a channel subject to errors and losses by managing acknowledgments, timers, and buffers.

## 🚀 Implemented Protocols

### 1. Utopian Protocol (`Utopian_snd.java` / `Utopian_rcv.java`)
* **Type:** Simplex (One-way), Error-free.
* **Mechanism:** Assumes an ideal channel and infinite buffers. The sender transmits data continuously without waiting for confirmation. The receiver accepts all data and sends simple ACKs, but there is no retransmission logic.

### 2. Simplex Protocol (`Simplex_snd.java` / `Simplex_rcv.java`)
* **Type:** One-way Stop-and-Wait.
* **Mechanism:**
    * **Sender:** Sends a packet and blocks until it receives the corresponding ACK or the timer expires (`handle_Data_Timer`).
    * **Receiver:** Validates the sequence number (`frame_expected`) before delivering to the network layer, discarding duplicates.

### 3. Stop & Wait (`StopWait.java`)
* **Type:** Bidirectional with Retransmission.
* **Features:**
    * **Piggybacking:** Acknowledgments (ACKs) are hitched onto data frames (`last_DataF_rcv.ack()`) to save bandwidth.
    * **Timers:** Uses data timers for retransmission and ACK timers to send explicit confirmations when there is no return traffic.

### 4. Go-Back-N (`GoBackN.java`)
* **Type:** Sliding Window.
* **Features:**
    * **Pipeline:** Allows sending multiple packets (up to `win_size`) before requiring acknowledgment.
    * **Error Handling:**
        * **NAKs:** Sends *Negative Acknowledgements* upon detecting gaps in the expected sequence to accelerate recovery (`send_NAK`).
        * **Rollback:** In case of error or timeout, the `roll_back_it` function resets transmission starting from the lost packet, discarding subsequent out-of-order packets.
    * **Sending Buffer:** Maintains a history (`sending_buffer`) of packets sent but not yet acknowledged.

### 5. Go-Back-N with Flow Control (`GoBackN_FlowC.java`)
* **Type:** Sliding Window with Buffer Management.
* **Improvement:** Adds logic to prevent receiver *buffer overflow*.
* **Mechanism:**
    * Monitors the receiver's buffer size (`rcvbufsize`) reported in frame headers.
    * Pauses transmission if the receiver is full (when `rcv_buff == 0`).
    * Resumes sending upon the `new_network_buffers` event, which signals that space has been freed.

## 🛠️ Structure and Utilities

* **`Base_Protocol.java`:** Base class that implements modular arithmetic for sequence numbers (functions `next_seq`, `prev_seq`, `between`, `diff_seq`) to correctly handle sequence wrap-around.
* **`Callbacks.java`:** Interface defining the methods for handling simulator events (frame arrival, timeouts, end of transmission, etc.).

## 👤 Authors

* **Sidi brahim**


---
*Project developed for the Computer Science / Electrical Engineering degree - FCT UNL.*
