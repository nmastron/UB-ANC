Copyright © 2014 - 2018 Jalil Modares

This program is part of my Ph.D. Dissertation research in the Department of Electrical Engineering at the University at Buffalo. I work in UB's Multimedia Communications and Systems Laboratory with my Ph.D. adviser, [Prof. Nicholas Mastronarde](http://www.eng.buffalo.edu/~nmastron).

This program is free software: you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, either version 3 of the License, or any later version.

This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public License for more details.

You should have received a copy of the **GNU General Public License** along with this program. If not, see <http://www.gnu.org/licenses/>.

# Designing Multi-Drone Networks and Applications
Buffalo's Airborne Networking and Communications Ecosystem (UB-ANC)

## Abstract
Recent advances in rotorcraft design, multi-rotor vehicle control, miniaturization of hardware, sensing, and battery technologies have enabled cheap, practical design of micro air vehicles (MAVs) for civilian and hobby applications. In parallel, several applications are being envisioned that bring together networks of MAVs to accomplish large tasks by coordinating with each other. Despite these advancements, and new FAA rules governing their use, it is still very challenging to experiment with multiple networked MAVs. To address this problem, we are engaged in a multi-year effort to develop an open software/hardware platform called the University at Buffalo's Airborne Networking and Communications Ecosystem (UB-ANC), which consists of three main open-source projects: **UB-ANC Drone**, [UB-ANC Emulator](https://github.com/jmodares/UB-ANC-Emulator), and [UB-ANC Planner](https://github.com/jmodares/UB-ANC-Planner). Our goal is to design, implement, and test MAV networking applications in simulation, and provide seamless transition to deployment.

## UB-ANC Drone
**UB-ANC Drone** is an open software/hardware platform that aims to facilitate rapid testing and repeatable comparative evaluation of airborne networking and communications protocols at different layers of the protocol stack. It combines quadcopters capable of autonomous flight with sophisticated command and control capabilities and embedded software-defined radios (SDRs), which enable flexible deployment of novel communications and networking protocols. This is in contrast to existing airborne network testbeds, which rely on standard inflexible wireless technologies, e.g., Wi-Fi or Zigbee. UB-ANC Drone is designed with emphasis on modularity and extensibility, and is built around popular open-source projects and standards developed by the research and hobby communities. This makes UB-ANC Drone highly customizable, while also simplifying its adoption. The [UB-ANC Agent](https://github.com/jmodares/UB-ANC-Agent), which is the software that controls the drone, is designed to be compatible with any flight controller that supports the popular Micro Air Vehicle Communications Protocol, [MAVLink](http://mavlink.org). With its modular design, UB-ANC Drone provides tools for networking researchers to study airborne networking protocols and robotics researchers to study mission planning algorithms without worrying about other implementation details. Furthermore, we envision that it will facilitate collaborative work between networking and robotics researchers interested in problems related to network topology control and managing trade offs between mission objectives and network performance.

## UB-ANC Emulator
[UB-ANC Emulator](https://github.com/jmodares/UB-ANC-Emulator) is an emulation environment created to design, implement, and test various applications (missions) involving one or more drones in software, and provide seamless transition to experimentation. [UB-ANC Emulator](https://github.com/jmodares/UB-ANC-Emulator) provides flexibility in terms of the underlying flight dynamics and network simulation models. By default, it provides low-fidelity flight dynamics and network simulation, thus high scalability (it can support a large number of emulated agents). Depending on the application, it can connect to a high-fidelity physics engine for more accurate flight dynamics of agents (drones). It can also connect to a high-fidelity network simulation to model the effect of interference, packet losses, and protocols on network throughput, latency, and reliability (e.g., we have integrated [ns-3](https://www.nsnam.org) into the emulator). Another important aspect of the [UB-ANC Emulator](https://github.com/jmodares/UB-ANC-Emulator) is its ability to be extended to different setups and connect to external communication hardware. This capability allows robotics researchers to emulate the mission planning part in software while the network researcher tests new network protocols on real hardware, or allows a network of real drones to connect to emulated drones and coordinate their tasks.

## UB-ANC Planner
Utilizing the UB-ANC Drone and [UB-ANC Emulator](https://github.com/jmodares/UB-ANC-Emulator) projects, we built an application for airborne networks, called [UB-ANC Planner](https://github.com/jmodares/UB-ANC-Planner). It considers the problem of covering an arbitrary area containing obstacles using multiple drones, i.e., the so-called **Coverage Path Planning (CPP)** problem. The goal of the CPP problem is to find paths for each drone such that the entire area is covered. However, a major limitation in such deployments is drone flight time. To most efficiently use a swarm, we propose to minimize the maximum energy consumption among all drones' flight paths. We perform measurements to understand energy consumption of a drone. Using these measurements, we formulate an **Energy Efficient Coverage Path Planning (EECPP)** problem. We solve this problem in two steps: a load-balanced allocation of the given area to individual drones, and a **Minimum Energy Path Planning (MEPP)** problem for each drone. We conjecture that the MEPP is NP-hard as it is similar to the **Traveling Salesman Problem (TSP)**. We propose an adaptation of the well-known **Lin-Kernighan Heuristic (LKH)** for the TSP to efficiently solve the problem. We compare our solution to the recently proposed depth-limited search with back tracking algorithm, the optimal solution, and rastering as a baseline. Results show that our algorithm is more computationally efficient and provides more energy-efficient solutions compared to the other heuristics.
