# ECE535 Final Project: Time Synchronization via Embedded Sensor Data
Aidan Chin, Robert Yao, Alexander Shub, Gerard DeCunha

## Motivation

Out of all the projects listed, this one stood out to our group as being the most suited for our areas of interest/expertise. We have lots of experience with basic microcontrollers such as the AVR platform and utilizing them for communication, so the task of creating a simple protocol seems like a natural extension of this interest. This is also a great opportunity for us to increase our knowledge and understand the way systems interact and the particular challenges that come with them. The project will also be a good exercise in networking separate systems on different platforms, namely edges with a central Pi running the algorithm. 

## Design Goals
- Develop a time synchronization protocol using timestamped sensor data from two embedded devices.
- The data will be transmitted to a Raspberry Pi, which will run the synchronization algorithm.
- Ensure accurate alignment of sensor events across devices despite network delay and clock drift.

## Deliverables

### • Hardware
- ESP32s connected to sensors

### • Software
- ESP32 Firmware: Sensor reading, timestamping, and transmission to Raspberry Pi
- Raspberry Pi Software: Data reception and synchronization algorithm

### • Documentation
- Setup and usage guide
- Final project report

### • Final Demonstration
- Live demo showing synchronized sensor data and protocol performance

## System Blocks

```mermaid
flowchart TD
 subgraph Programming["Programming"]
        RPI_USB["Raspberry Pi USB Port"]
        ESP_PROG["ESP32 Programming Port UART/USB"]
  end
    PWR["Power Supply"] --> RPI["Raspberry Pi"] & ESP["ESP32"] & Sensor["Sensor (TBD)"]
    RPI <==> ESP
    ESP <--> Sensor
    RPI_USB --- RPI
    ESP_PROG --- ESP


     RPI_USB:::Aqua
     ESP_PROG:::Rose
     RPI:::Aqua
     ESP:::Rose
    classDef Aqua stroke-width:1px, stroke-dasharray:none, stroke:#46EDC8, fill:#DEFFF8, color:#378E7A
    classDef Rose stroke-width:1px, stroke-dasharray:none, stroke:#FF5978, fill:#FFDFE5, color:#8E2236
```
```mermaid
flowchart LR
 subgraph RPI["Raspberry Pi"]
        TS["Time Sync Protocol"]
        RPI_COMM["Communication Thread"]
  end
 subgraph ESP["ESP32"]
        ESP_COMM["Communication Thread"]
        SENSOR["Sensor Communication"]
  end
    TS <--> RPI_COMM
    ESP_COMM <--> SENSOR
    RPI_COMM <--> ESP_COMM


     TS:::Aqua
     RPI_COMM:::Pine
     RPI_COMM:::Peach
     ESP_COMM:::Peach
     SENSOR:::Rose
    classDef Aqua stroke-width:1px, stroke-dasharray:none, stroke:#46EDC8, fill:#DEFFF8, color:#378E7A
    classDef Rose stroke-width:1px, stroke-dasharray:none, stroke:#FF5978, fill:#FFDFE5, color:#8E2236
    classDef Pine stroke-width:1px, stroke-dasharray:none, stroke:#254336, fill:#27654A, color:#FFFFFF
    classDef Peach stroke-width:1px, stroke-dasharray:none, stroke:#FBB35A, fill:#FFEFDB, color:#8F632D

```
## HW/SW Requirements

| Component       | Purpose                                  |
|----------------|-------------------------------------------|
| ESP32           | Edge device for sensor data + timestamping |
| Raspberry Pi    | Central node for synchronization algorithm |
| Sensors         | Event generation for time sync testing     |
| C++             | ESP32 firmware development                 |
| Python          | Raspberry Pi software + algorithm          |

## Team Member Responsibilities

| Member           | Responsibilities                          |
|------------------|-------------------------------------------|
| Gerard DeCunha   | Software, writing, research                |
| Alexander Shub   | Networking, writing, research              |
| Aidan Chin       | Algorithm design, writing, hardware        |
| Robert Yao       | Setup, software, hardware                  |

## Project Timeline

```mermaid
gantt
    title ECE535 Project Timeline
    dateFormat YYYY-MM-DD
    section Setup
        Research                      :research, 2025-10-01, 7d
        Hardware Setup                :after research, 7d
        Software Setup                :setup, after research, 7d
        Check in 1                    :milestone, m1, 2025-10-01, 1d
    section Core Functionality
        Edge Node Firmware (ESP32)    :task3, after setup, 10d
        Gateway Software (RPi)        :task4, after setup, 10d
        System Integration & Logging  :task5, after task3, 4d
        Check in 2                    :milestone, m2, 2025-11-01, 1d
    section Algorithm Development
        Data Analysis & Initial Model :task6, after task5, 7d
        Deliverable 1 Network Delay   :task7, after task6, 7d
        Deliverable 2 Clock Drift     :task8, after task7, 7d
        Check in 3                    :milestone, m3, 2025-12-01, 1d
    section Finalization
        Code Cleanup & Documentation  :task9, after task8, 5d
        Final Report & Presentation   :task10, after task8, 7d
```

## References
- HAEST: Harvesting Ambient Events to Synchronize Time across Heterogeneous IoT Devices
- Automated Synchronization of Driving Data Using Vibration and Steering Events
- Exploiting Smartphone Peripherals for Precise Time Synchronization
