# CEG3006 V2P Safety Project

## System Integration
### Brief Description of the Solution

Smart Priority V2P Safety System

The proposed solution is a Vehicle-to-Pedestrian (V2P) safety application designed to improve road safety for vulnerable pedestrians, especially students in school zones, elderly users, and persons with disabilities, including physical, visual, and cognitive conditions. The system enables direct real-time communication between pedestrian smartphones and nearby vehicles to improve driver awareness and reduce accident risks at zebra crossings, blind spots, and other high-risk areas.

The application operates in two modes: pedestrian mode and vehicle mode. In pedestrian mode, the smartphone detects the pedestrian’s location and movement, then transmits safety information when the user approaches a crossing or other high-risk zone. In vehicle mode, the onboard unit receives this information, combines it with vehicle data such as speed, heading, and position, and assesses whether a collision risk exists. If a hazard is detected, the system issues an audio warning to the driver. This keeps the warning process focused on the driver, who is in the best position to take immediate action.

To avoid unnecessary distraction, the pedestrian’s smartphone operates mainly in the background as a silent safety transmitter. A key feature of the system is its priority-based warning logic. During profile setup, users can be assigned a verified priority class so that vulnerable groups such as school children, elderly pedestrians, wheelchair users, and visually impaired users receive stronger protection. When such users are detected, nearby vehicles trigger earlier or stronger driver warnings to encourage more cautious driving behavior.

Unlike traditional pedestrian detection systems that rely only on onboard sensors such as cameras or radar, this solution uses direct pedestrian-to-vehicle communication, which can improve detection reliability in low-visibility, obstructed, or crowded environments. While similar V2P concepts have been explored in cooperative intelligent transportation systems (C-ITS), this proposal emphasizes accessibility, vulnerability-based prioritization, and smartphone-based deployment, making it a practical and scalable solution for urban safety applications.

## Project Idea
This project explores a Vehicle-to-Pedestrian (V2P) communication system designed to improve safety for pedestrians and cyclists.

The goal is to design a system where pedestrians can broadcast their presence to nearby vehicles, allowing drivers to receive warnings when a potential collision risk is detected.

## Planned System Architecture
### Components
Pedestrian-side subsystem
Smartphone app, sensors, profile manager, and message generation

Pedestrian-to-vehicle communication subsystem
Direct C-V2X PC5 link that carries pedestrian awareness messages to nearby vehicles

Vehicle-side processing subsystem
Onboard receiver, message decoder, collision-risk assessment, and priority logic

In-vehicle warning subsystem
In-vehicle controller/network that sends the warning to the driver interface, such as dashboard, buzzer, or ADAS warning display

### System Architecture
#### A. Pedestrian-side subsystem
This subsystem is the origin of the safety message.
Its job is to sense the pedestrian’s situation and convert it into a form the vehicle can understand.

##### Main Components
- Smartphone application
- Positioning and motion sensors
- User profile (where priority is decided)
- Message generation module (alert system)

##### What it does
The pedestrian carries a smartphone with the V2P app installed.
The app continuously monitors basic movement and location information, such as:
- current position
- walking speed
- movement direction
- whether the user is near a school-zone crossing or zebra crossing

The app also stores a priority profile for the pedestrian.
- students in school zones
- elderly pedestrians
- persons with disabilities, including physical, visual, and cognitive conditions

This priority profile is important because it changes how cautiously the system behaves.
A higher-priority pedestrian causes the vehicle to react earlier or with a stronger warning.

##### Why a smartphone makes sense
A smartphone is a realistic pedestrian device because it already contains:
- GNSS / location functions
- motion sensors
- local processing capability
- a user interface for registration and alerts

#### B. Pedestrian-to-vehicle communication system
This subsystem is the direct wireless safety link between the pedestrian and the vehicle.

##### Main technology
- C-V2X
- PC5 interface for direct real-time safety communication
- Uu interface for backend synchronization and live updates

##### What it does
The communication subsystem allows the pedestrian’s smartphone to exchange information with the wider V2P system using two different interfaces with different purposes.

- PC5 is used for the live safety function of the system. Through PC5, the pedestrian’s smartphone sends safety-related messages directly to nearby vehicles. This direct path is used for time-critical situations where a vehicle must be warned immediately, such as at zebra crossings or in school zones.
- Uu is used for non-time-critical support functions. This includes backend synchronization, user profile updates, zone or map updates, system configuration updates, and optional cloud-based services.

In this design, the two interfaces are not treated as interchangeable. Instead, each is assigned a specific role:
- PC5 handles urgent, local, real-time safety communication
- Uu handles network-based backend communication and live service updates

##### Important assumption
A clear assumption is made in this project that the pedestrian smartphone is capable of PC5-based direct C-V2X communication.

This assumption is necessary because PC5 is not yet widely available as a standard feature in mainstream consumer smartphones. Therefore, whenever PC5 is mentioned in this project, it should be understood as an assumed capability for a future-ready or specialized smartphone platform.

By contrast, Uu-based communication is treated as realistic using existing mobile network connectivity, since normal cellular communication is already common on modern smartphones.

##### Why PC5 is the core choice
The main purpose of this project is to support:
- direct pedestrian-to-vehicle warning
- zebra crossing safety
- school-zone safety
- fast warning in short decision windows

Because of this, the main warning path should be direct and local, rather than dependent on routing through the wider mobile network. This is why PC5 is chosen as the primary interface for the live safety component of the system.

Using PC5 allows nearby vehicles to receive pedestrian safety messages quickly, which is important for situations where the driver must react immediately.

##### What message is transmitted
The pedestrian smartphone periodically generates and transmits a pedestrian awareness message. This message may include:
- temporary session ID
- current location
- walking speed
- movement direction
- crossing status
- priority category
- zone type

These messages allow the receiving vehicle to determine whether the pedestrian is nearby, whether the pedestrian is in a vulnerable group, and whether there is a possible collision risk.

##### Role of Uu in the architecture
The Uu interface is not used as the main urgent warning path in this project.

Instead, Uu is used as a support communication channel for functions such as:
- pedestrian profile synchronization
- school-zone or map database updates
- system configuration updates
- cloud logging and analytics
- live backend service updates

#### C. Vehicle-side processing subsystem
This subsystem is the decision-making core of the system. Its role is to receive the pedestrian’s live safety message, interpret the data, assess the level of risk, and decide whether a warning should be issued to the driver.

##### Main Components
- C-V2X receiver / onboard unit
- PC5 message reception module
- Message decoder
- Priority evaluation module
- Collision-risk assessment module
- Warning decision logic

##### What it does
When the vehicle receives a pedestrian awareness message, it must determine whether the pedestrian poses a possible collision risk.

So the vehicle-side subsystem performs four main tasks:
##### 1. Message reception
The vehicle’s onboard unit receives the pedestrian’s live safety message over PC5.

Assumption:
The vehicle is equipped with a C-V2X-capable onboard unit (OBU) that can receive PC5-based pedestrian safety messages. While such capability exists in some conneted-vehicle deployments, it is not assumed to be standard in all consumer vehicles today. Therefore, this project treats the OBU as an available vehicle-side component within the propsed system architecture.

This is the primary real-time input used by the vehicle to detect nearby vulnerable pedestrians in situations such as:
- zebra crossings
- school zones
- blind spots
- unexpected crossing movement

##### 2. Message decoding
The received message is decoded to extract relevant pedestrian information, such as:
- pedestrian position
- walking direction
- walking speed
- priority class
- crossing state
- zone type

This information allows the vehicle to understand not only where the pedestrian is, but also whether the pedestrian belongs to a higher-priority vulnerable group.

##### 3. Risk assessment
The vehicle then compares the pedestrian’s live state with vehicle-side data, such as:
- vehicle speed
- vehicle heading
- vehicle position
- distance to crossing
- estimated arrival time at the crossing

Using these inputs, the system estimates whether the pedestrian and vehicle are likely to enter the same conflict zone within the next few seconds.

##### 4. Priority-aware decision making
The system does not treat all pedestrians equally.
If the pedestrian is classified as high priority, the warning threshold becomes more conservative.

For example:
- a student in a school zone may trigger an earlier warning
- an elderly pedestrian may trigger a larger safety buffer
- a wheelchair user or other disabled pedestrian may cause the system to assume slower crossing speed and longer crossing time

So the vehicle-side controller is not just a receiver.
It is the intelligence layer that turns live pedestrian data into a warning decision.

#### D. In-vehicle warning subsystem
This subsystem is the final response layer. Its purpose is to ensure that once a risk has been detected, the driver receives a warning in a clear and timely manner.

##### Main components
- V2P warning controller
- CAN bus
- driver HMI

##### What it does
After the vehicle-side processing subsystem detects a risk using the live PC5 safety message, the warning must be delivered to the driver through the vehicle’s internal systems.

This means:
- PC5 is used only for external pedestrian-to-vehicle safety communication
- once the risk is confirmed, the warning is transferred internally through the in-vehicle network
- CAN bus is used as the main internal communication path for warning delivery

##### What CAN does in the system
Once the vehicle controller determines that a warning is necessary, it sends an internal warning message across the vehicle network to one or more endpoints, such as:
- instrument cluster
- dashboard warning light
- buzzer
- ADAS display
- steering or seat alert module

The system can define multiple driver-warning levels:
Level 1: pedestrian detected nearby
Level 2: high-priority pedestrian approaching crossing
Level 3: immediate collision risk

This is where the priority logic becomes visible to the driver.

For example:
- a normal pedestrian may trigger a Level 1 or Level 2 alert
- a student in a school zone, elderly pedestrian, or disabled pedestrian may trigger an earlier or stronger Level 2 or Level 3 alert

### Hardware components and parameters
<img width="1269" height="335" alt="image" src="https://github.com/user-attachments/assets/9bf2592c-04d0-462c-9258-63fc18ff282b" />
[Table 1: BLE vs. C-V2X]

<img width="987" height="190" alt="image" src="https://github.com/user-attachments/assets/5526cfbe-a6b6-44a6-a6ff-b282e9af19f4" />
[Table 2: C-V2X PC5 vs. C-V2X Uu]

### Use case
A car is travelling along an urban road toward a zebra crossing near a residential area. At the same time, a pedestrian with a verified priority profile, such as a wheelchair user or a person with visual or cognitive disabilities, is approaching the crossing while carrying a smartphone running the Smart Priority V2P Safety System. The smartphone silently transmits the pedestrian’s location, movement, and priority status to nearby vehicles through direct V2P communication.

The vehicle’s onboard unit receives this safety message and combines it with vehicle data such as speed, heading, and position to assess collision risk. Because the pedestrian belongs to a high-priority vulnerable group, the system applies a more cautious warning threshold. As the car approaches the same conflict zone, the system detects potential risk and issues an audio warning to the driver, such as “Warning. Vulnerable pedestrian ahead.”

This early warning allows the driver to slow down and prepare to stop before reaching the crossing. In this way, the system improves protection for pedestrians who may need more time, space, and caution from approaching vehicles.

### Simple illustration
<img width="857" height="895" alt="ceg3006_project" src="https://github.com/user-attachments/assets/26b8d8ac-de7a-4e02-a135-032a249a2979" />

## AI Usage
### ChatGPT:
Prompting AI to find keywords for searching relevant topics and technologies

Input:
<img width="827" height="1006" alt="image" src="https://github.com/user-attachments/assets/94145a4c-5d79-4859-a90a-3ebfaf05ffe3" />

Output:
<img width="900" height="946" alt="image" src="https://github.com/user-attachments/assets/e6685837-5f23-4c3c-a3c9-d0aacef667bc" />
<img width="900" height="684" alt="image" src="https://github.com/user-attachments/assets/8f525fbf-f3ee-41e8-8fd8-560985cf3c7d" />
<img width="900" height="864" alt="image" src="https://github.com/user-attachments/assets/b6dcc31f-d14c-44ba-ab1d-a774edd367f2" />

## Repository Structure

/CEG3006_flowchart.png

/DecisionLog.md
- project development decisions
