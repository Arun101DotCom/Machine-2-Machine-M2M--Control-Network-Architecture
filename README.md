# Machine-2-Machine-M2M--Control-Network-Architecture
Implementation of a Machine-to-Machine (M2M) framework using Raspberry Pis and the OSI model. Features a multi-homed network architecture with custom routing and packet analysis (tcpdump). Includes a closed-loop DC motor control system using PID algorithms to mitigate network latency and stabilize real-time hardware performance.

# M2M Communication Architecture & DC Motor Control
This project demonstrates a Machine-to-Machine (M2M) communication framework implemented across a distributed Raspberry Pi network. It covers network configuration, packet analysis, and the design of a closed-loop control system for a DC motor.

## 🌐 Network Architecture
The system utilizes four Raspberry Pis (A, B, C, D) configured with **multi-homing** to bridge three separate LAN segments. 

- **Gateways:** Configured using `route add` to enable inter-LAN communication.
- **Analysis:** Used `tcpdump` for datagram inspection and `traceroute` for hop path determination.
- **Protocol:** Heavy focus on ICMP (Ping) and TCP/IP stack layers.


## ⚙️ DC Motor Control System
A real-time control system was developed to manage motor speed and direction via a feedback loop.

### PID Control
To address network latency (especially when the controller and encoder are on different devices), we implemented a **PID (Proportional-Integral-Derivative)** controller.

$$u(t) = K_p e(t) + K_i \int e(t) dt + K_d \frac{de(t)}{dt}$$

- **Input:** 500-slot optical encoder (IR LED + Photo Diode).
- **Output:** DC Motor driver via RS232 Serial.
- **Stability:** Analyzed how network latency affects the stability of the feedback loop.



## 🛠 Key Commands Used
- `ifconfig` / `arp`: Interface and MAC address management.
- `tcpdump -c 5`: Datagram packet analysis.
- `route add -net`: Manual routing table configuration for multi-homing.
- `gnuplot`: Visualization of motor step response and PID tuning.

## 📂 Project Structure
- `/network_configs`: Interface files and routing scripts.
- `/src_control`: C/C++ code for the Encoder and PID Controller.
- `/analysis`: Tcpdump logs and GnuPlot script results.
  
* 01_Technical Report
* 02_Output Data

**Author:** Arun Chakkyadath Chandran 
