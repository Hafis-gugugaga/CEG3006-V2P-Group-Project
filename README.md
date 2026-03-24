# CEG3006 V2P Safety Project

## System Integration
### Brief Description of the Solution

Smart Priority V2P Safety System

The proposed solution is a Vehicle-to-Pedestrian (V2P) safety application designed to improve road safety for vulnerable pedestrians, especially students in school zones, elderly users, and person with disabilities, including physical, visual, and cognitive conditions. The system allows direct real-time communication between pedestrian smartphones and nearby vehicles to improve driver awareeness and reduce accident risks at zebra crossings, blind spot, and other high-risk areas.

[To be refined]
The application operates in two modes: pedestrian mode and vehicle mode. Pedestrian devices continuously broadcast location and status information using short-range wireless communication (e.g., Bluetooth Low Energy or Cellular V2X). When a pedestrian approaches a crossing, the system sends alerts to nearby vehicles. Drivers receive warnings if pedestrians are crossing unexpectedly, approaching blind spots, or jaywalking. At the same time, pedestrians receive vibration or sound notifications when vehicles are approaching.

To prevent unnecessary distractions, the application minimizes visual notifications on the pedsterian's device and continues transmitting safety information in the background. A key feature of the system is its priority-based warning logic. Users can register a pedestrian profile, allowing the system to assign higher priority to vulnerable groups such as school children, elderly pedestrians, wheelchair users, and visually impaired users. When such users are detected, vehicles receive earlier or stronger alerts to encourage more cautious driver response.

Unlike traditional pedestrian detection systems that rely only on onboard sensors such as cameras or radar, this solution uses direct pedestrian-to-vehicle communication, which can improve detection reliability in low-visibility, obstructed, or crowded environments. While similar V2P concepts have been studied in cooperative intelligent transportation systems (C-ITS), this proposal focuses on accessibility, vulnerability-based prioritization, and smartphone-based deployment, making it a practical and scalable solution for urban safety applications.

## Project Idea
This project explores a Vehicle-to-Pedestrian (V2P) communication system designed to improve safety for pedestrians and cyclists.

The goal is to design a system where pedestrians can broadcast their presence to nearby vehicles, allowing drivers to receive warnings when a potential collision risk is detected.

## Planned System Architecture
Pedestrian-side subsystem
Smartphone app, sensors, profile manager, and message generation

Pedestrian-to-vehicle communication subsystem
Direct C-V2X PC5 link that carries pedestrian awareness messages to nearby vehicles

Vehicle-side processing subsystem
Onboard receiver, message decoder, collision-risk assessment, and priority logic

In-vehicle warning subsystem
In-vehicle controller/network that sends the warning to the driver interface, such as dashboard, buzzer, or ADAS warning display

## Repository Structure

docs/
    system architecture diagrams

research/
    literature review and references

DecisionLog.md
    project development decisions

## Next Steps

- Research existing V2P technologies
- Design system architecture
- Define communication protocol
- Create system diagrams
