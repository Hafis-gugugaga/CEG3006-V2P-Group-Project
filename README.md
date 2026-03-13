# CEG3006 V2P Safety Project

## System Integration
### Brief Description of the Solution

Smart Priority V2P Safety System

The proposed solution is a Vehicle-to-Pedestrian (V2P) safety application designed to protect vulnerable pedestrians, such as individuals with physical disabilities, visual impairments, cognitive spectrum conditions, and elderly users. The system enables real-time communication between pedestrian smartphones and nearby vehicles to improve awareness and reduce accident risks at crossings and blind spots.

The application operates in two modes: pedestrian mode and vehicle mode. Pedestrian devices continuously broadcast location and status information using short-range wireless communication (e.g., Bluetooth Low Energy or Cellular V2X). When a pedestrian approaches a crossing, the system sends alerts to nearby vehicles. Drivers receive warnings if pedestrians are crossing unexpectedly, approaching blind spots, or jaywalking. At the same time, pedestrians receive vibration or sound notifications when vehicles are approaching.

To prevent unnecessary distractions, the application only sends visible notifications when the pedestrian's screen is active; otherwise, it continues transmitting safety data silently. Users can create pedestrian profiles, allowing the system to prioritize individuals with higher vulnerability, such as wheelchair users or visually impaired pedestrians. Vehicles receive stronger alerts when these high-priority users are detected near crossings.

Unlike traditional pedestrian detection systems that rely solely on vehicle sensors such as cameras or radar, this system enables direct communication between pedestrians and vehicles, improving detection reliability in low visibility or crowded environments. Similar V2P concepts have been explored in cooperative intelligent transportation systems (C-ITS), but this proposal emphasizes user prioritization, accessibility features, and smartphone-based implementation, making it more scalable and accessible for urban environments.

## Project Idea
This project explores a Vehicle-to-Pedestrian (V2P) communication system designed to improve safety for pedestrians and cyclists.

The goal is to design a system where pedestrians can broadcast their presence to nearby vehicles, allowing drivers to receive warnings when a potential collision risk is detected.

## Planned System Architecture
Components of the proposed system:

- Pedestrian device (smartphone)
- Wireless communication between pedestrian and vehicle via traffic system (pedestrian -> traffic system -> vehicle)
- Vehicle onboard receiver
- Collision risk detection algorithm (AI prediction)
- Driver warning alerts

## Repository Structure

docs/
    system architecture diagrams

research/
    literature review and references

decision-log/
    project development decisions

## Next Steps

- Research existing V2P technologies
- Design system architecture
- Define communication protocol
- Create system diagrams
