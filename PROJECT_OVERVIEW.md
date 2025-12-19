# Mobile Computing Project – 5G Network Slicing Framework

## 1. Project Overview

This project implements a **5G Network Management Framework** that enables the **selection, activation, and simultaneous operation of multiple 5G use cases**.  
Based on the selected use cases, the framework automatically configures the underlying 5G network by adjusting **network slices, priorities, bit rates, and data paths**.

The project is implemented using **Open5GS** as the 5G core network and **UERANSIM / PacketRusher** for RAN and UE simulation.  
A **web-based UI** is developed to control the network, activate use cases, and visualize the system state.

---

## 2. Motivation and Background

5G networks are designed to support **heterogeneous application scenarios** with very different requirements.  
Examples include:

- high-bandwidth mobile broadband users,
- latency-critical services such as connected cars or emergency communication,
- large-scale IoT deployments with many low-data-rate devices.

A single static network configuration cannot efficiently serve all these use cases at the same time.  
Therefore, **network slicing** is used to create multiple logical networks (slices) on top of a shared physical infrastructure.

This project demonstrates how such a slicing-based approach can be **managed dynamically** through a framework that links **use-case selection** with **automatic network reconfiguration**.

---

## 3. Selected Use Cases and Slices

To balance complexity and clarity, **three representative 5G use cases** are selected.  
Each use case is mapped to a dedicated network slice.

### 3.1 Mobile Broadband (eMBB)
- Typical smartphone voice and data services
- High throughput
- Normal priority

### 3.2 Connected Cars / Emergency Services (URLLC)
- Latency-critical and mission-critical communication
- Very low latency
- Highest priority

### 3.3 Industrial IoT / Smart City (mIoT)
- Large number of low-data-rate devices
- Low bandwidth
- Lowest priority

These three slices cover the **three main 5G service classes**: eMBB, URLLC, and mMTC.

---

## 4. Deployment Focus

The project focuses on a **Network Slicing Deployment**.

Key characteristics:
- One physical 5G infrastructure
- Multiple logical slices using **S-NSSAI**
- Slice-specific QoS parameters (latency, bandwidth, priority)
- Simultaneous activation of multiple use cases

The deployment is containerized using Docker and orchestrated via configuration files and scripts.

---

## 5. System Architecture

The system consists of the following main components:

### 5.1 5G Core Network
- Open5GS core functions (AMF, SMF, UPF, NRF, NSSF)
- Slice-aware configuration
- Multiple slice profiles mapped to UEs

### 5.2 RAN and UE Simulation
- UERANSIM or PacketRusher for gNB and UE simulation
- Multiple UEs assigned to different slices

### 5.3 Transport Network
- QoS enforcement using traffic control mechanisms
- Bandwidth and priority differentiation per slice

### 5.4 Backend Control Layer
- Controls network functions and slice configurations
- Applies configuration changes dynamically
- Provides status information to the UI

### 5.5 Web-Based User Interface
- Allows selection of use cases
- Starts and stops network functions
- Visualizes network topology and slice status

---

## 6. Dynamic Use Case Activation

The core functionality of the framework is the **dynamic activation of use cases**:

1. The user selects one or more use cases in the UI.
2. The backend determines the required slices and parameters.
3. The network is automatically reconfigured:
   - slices are activated,
   - QoS parameters are applied,
   - UEs are mapped to slices.
4. The network runs multiple use cases simultaneously with proper isolation.

This behavior directly implements the requirement that the network should **automatically adjust priorities, bit rates, and data paths based on the selected use cases**.

---

## 7. Automated Testing and Verification

To verify correct behavior, the framework includes **automated tests**, such as:

- latency measurements per slice,
- throughput measurements per slice,
- verification of UE registration and session establishment,
- slice isolation tests ensuring traffic separation.

Test results are used to validate that each slice meets its intended performance characteristics.

---

## 8. Documentation and Demo

The final project deliverables include:

- architecture and design documentation,
- configuration and setup instructions,
- test descriptions and results,
- a user manual for the framework,
- a recorded demo showing:
  - use-case selection,
  - slice activation,
  - network operation,
  - automated testing.

---

## 9. Project Goal

The goal of this project is to demonstrate a **realistic and practical 5G network slicing framework** that:

- supports multiple use cases simultaneously,
- dynamically adapts the network configuration,
- provides clear visualization and control,
- and validates behavior through automated testing.

This project highlights the importance of **network slicing and automation** in modern 5G systems.
