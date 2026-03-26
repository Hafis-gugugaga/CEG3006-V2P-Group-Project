# CEG3006 V2P Safety Project

## System Integration
### Brief Description of the Solution

Smart Priority V2P Safety System

The proposed solution is a Vehicle-to-Pedestrian (V2P) safety application designed to improve road safety for vulnerable pedestrians, especially students in school zones, elderly users, and persons with disabilities, including physical, visual, and cognitive conditions. The system enables direct real-time communication between pedestrian smartphones and nearby vehicles to improve driver awareness and reduce accident risks at zebra crossings, blind spots, and other high-risk areas.

The application operates in two modes: pedestrian mode and vehicle mode. In pedestrian mode, the smartphone detects the pedestrian’s location and movement, then transmits safety information when the user approaches a crossing or other high-risk zone. In vehicle mode, the onboard unit receives this information, combines it with vehicle data such as speed, heading, and position, and assesses whether a collision risk exists. If a hazard is detected, the system issues an audio warning to the driver. This keeps the warning process focused on the driver, who is in the best position to take immediate action.

To avoid unnecessary distraction, the pedestrian’s smartphone operates mainly in the background as a silent safety transmitter. A key feature of the system is its priority-based warning logic. During profile setup, users can be assigned a verified priority class so that vulnerable groups such as school children, elderly pedestrians, wheelchair users, and visually impaired users receive stronger protection. When such users are detected, nearby vehicles trigger earlier or stronger driver warnings to encourage more cautious driving behavior.

Unlike traditional pedestrian detection systems that rely only on onboard sensors such as cameras or radar, this solution uses direct pedestrian-to-vehicle communication, which can improve detection reliability in low-visibility, obstructed, or crowded environments. While similar V2P concepts have been explored in cooperative intelligent transportation systems (C-ITS), this proposal emphasizes accessibility, vulnerability-based prioritization, and smartphone-based deployment, making it a practical and scalable solution for urban safety applications.

## Literature Review
Vehicle-to-Pedestrian (V2P) communication has been widely explored as a way to improve road safety, especially for pedestrians and cyclists. Most existing solutions focus on enabling communication between pedestrians and vehicles so that potential collisions can be detected earlier than with traditional onboard sensors like cameras or radar. However, current implementations still show limitations, particularly in terms of real-world usability and adaptability.

One of the more practical approaches is smartphone-based V2P systems. In the work by Gelbal et al. (2024), a mobile application was developed where pedestrians broadcast their position, speed and direction using Bluetooth Low Energy (BLE). The vehicle then uses this data to estimate collision risk using a Time-To-Zone (TTZ) model, which triggers warning alerts for the driver. This approach was also tested in situations where there is no line of sight to the pedestrians such as when they are hidden behind obstacles. It shows that communication-based systems can still detect risks even when cameras may not be able to see these pedestrians (Gelbal et al., 2024). The drawback of the system is that it relies on simple calculations and treats all pedestrians the same. The system does not consider differences in age, mobility or reaction capability, which can affect how dangerous a situation actually is.

Broader studies on V2X communication highlight additional challenges. Position accuracy turns out to be a big limitation in these systems. Current smartphones use GNSS despite the accuracy not being as reliable, especially in urban areas. Buildings can block signals or cause reflections, so the location data can end up being off (De Ponte Müller et al., 2022).Due to this limitation, the system might not always predict collision risks correctly.

Technologies like ITS-G5 and C-V2X are usually preferred since they can send data very quickly, which is important for safety but they do not always work well over longer distances and may require certain setups. LTE works over a wider area, but the delay is slightly higher, which can be a problem in time-sensitive situations. So in most cases, there’s a trade-off, and it’s hard to get speed, reliability, and coverage all at once.

Another approach is to use infrastructure to help with detection where roadside units with sensors like cameras or radar can detect pedestrians and send that information to vehicles using Cooperative Perception Messages (CPMs). This works better in places like intersections or blind spots where direct communication might not always happen (De Ponte Müller et al., 2022). The downside is that these systems are costly and not easy to deploy everywhere.

Some studies also look at combining different parts into one system. Arena et al. (2020) describe a setup where the vehicle uses its onboard sensors to collect data and then communicates with both infrastructure and pedestrian smartphones. The pedestrian’s phone can also pick up on behaviour, like whether the user is distracted and adjust alerts based on that. This makes the system a bit more focused on how people actually behave, rather than just relying on technical detection (Arena et al., 2020). However, such systems are often conceptual and add complexity in terms of integration, communication reliability, and energy consumption.

Across these studies, most V2P systems focus on detecting collisions and issuing warnings based on distance, speed, and trajectory. While this works to some extent, it results in a one-size-fits-all approach where all pedestrians are treated the same. In reality, different groups have different levels of vulnerability. For example, a child or an elderly person will likely react slower than a healthy adult. Most systems do not account for this, which reduces their effectiveness in real-world situations.
Another limitation is that many systems stop at basic warning generation. This can lead to drivers becoming used to alerts and eventually ignoring them, especially if they do not seem urgent. At the same time, pedestrian alerts are often not very accessible, as they rely mainly on visual cues that may not work for all users.

Although smartphone-based systems are more scalable, they still depend on user participation and device performance. Battery usage, background restrictions and sensor accuracy can affect reliability. Infrastructure-based systems reduce reliance on user devices but are harder to deploy widely. This shows a gap between what works in theory and what can realistically be implemented in everyday environments.
Overall, while V2P systems have improved, they still mainly focus on detection and basic warnings. They do not consider differences in pedestrian vulnerability, meaning all users are treated the same. This suggests a need for more context-aware V2P systems that can prioritise safety based on the characteristics of different road users.

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
AI was used for further idealization and language correction / clarification.

#### Prompt 1
##### Input:
<img width="827" height="1006" alt="image" src="https://github.com/user-attachments/assets/94145a4c-5d79-4859-a90a-3ebfaf05ffe3" />

##### Output:
<img width="900" height="946" alt="image" src="https://github.com/user-attachments/assets/e6685837-5f23-4c3c-a3c9-d0aacef667bc" />
<img width="900" height="684" alt="image" src="https://github.com/user-attachments/assets/8f525fbf-f3ee-41e8-8fd8-560985cf3c7d" />
<img width="900" height="864" alt="image" src="https://github.com/user-attachments/assets/b6dcc31f-d14c-44ba-ab1d-a774edd367f2" />

#### Prompt 2
##### Input:
<img width="790" height="1234" alt="image" src="https://github.com/user-attachments/assets/3a50c949-3875-4052-9635-58182f815392" />

##### Output:
<img width="737" height="435" alt="image" src="https://github.com/user-attachments/assets/c1052a76-9b6b-45a7-853e-c78cb73086a6" />
<img width="732" height="923" alt="image" src="https://github.com/user-attachments/assets/5be510e7-abe6-4505-a8aa-ca0bea680d23" />

Idea relevance check + Advice

#### Prompt 3
##### Input:
<img width="534" height="180" alt="image" src="https://github.com/user-attachments/assets/aa208527-accf-4dd0-b279-fc48dd8f2225" />

##### Output:
<img width="700" height="721" alt="image" src="https://github.com/user-attachments/assets/1e7fc1f2-b30b-4f15-a01d-1ad3fda31294" />

### Identified weaknesses or hallucinations
#### 1.
One weakness identified in the AI-generated suggestions was that, although the AI was effective at proposing technically interesting features and system ideas, it did not always fully consider practical implementation constraints and the user’s point of view. For example, an earlier suggestion proposed sending alerts to both pedestrians and drivers. While this sounded reasonable from a general safety perspective, it was less suitable for the intended target users of this project, especially persons with disabilities or cognitive conditions, since the driver is the one in the best position to take immediate action. This showed that AI can generate many possible ideas quickly, but those ideas still require human judgment to evaluate whether they are practical, accessible, and appropriate for the real-world users of the system.

#### 2.
Although the AI could suggest ideas quickly, it often stayed too general unless guided with specific questions and technical keywords. More useful responses were obtained only after prompting with focused terms such as C-V2X, PC5, Uu, and OBU. This shows that AI can assist with exploration, but it still relies heavily on the user to steer it toward the depth and direction required.

#### 3.
So far, no obvious hallucinations were identified in the AI-generated responses, as the points provided were generally supported by cited sources. This made the information more trustworthy and easier to verify during the design process. However, the presence of sources did not automatically guarantee that every suggestion was fully suitable for the project. The responses still needed to be checked for relevance, practicality, and alignment with the project scope. Therefore, although no major hallucinations were encountered, human review was still necessary to confirm that the information was accurate and appropriate for the intended application.

## Individual Reflection and Contribution
### Yejin – Use Case Design and Scenario Development
My main contribution was helping to develop the use case and practical scenario for how the proposed V2P system would function in a real road environment. While researching the project together as a team, I developed a stronger understanding of how V2P communication can improve road safety by allowing earlier awareness between pedestrians and vehicles. I learned that this is especially useful in situations where drivers may not immediately notice a pedestrian through vision alone. In my role, I focused more on how this concept could be applied to a realistic crossing scenario, including how a vulnerable pedestrian approaching a crossing could trigger a warning to a nearby vehicle. This helped me better understand that V2P is not only a technical communication concept, but also a practical safety solution that must fit real traffic situations. I also realised that a strong use case is important because it helps explain clearly how the system would function from start to end. Through this experience, I improved my ability to translate a technical idea into a more realistic and meaningful application. Overall, the project deepened my understanding of how V2P can support preventive road safety.

### Gia Minh – System Concept and Functional Flow
My contribution to the project was mainly in helping to explain the system concept and functional flow of the proposed V2P system. Like the rest of the team, I was involved in understanding the V2P idea through our shared research and discussions. From this, I learned that V2P is valuable because it allows information about pedestrian presence to be communicated, processed, and turned into an earlier warning for the driver. My focus was on understanding how the different parts of the system work together, from the pedestrian side to the vehicle side, and how the communication flow supports timely decision-making. This made me realise that V2P is not simply about sending data, but about turning communication into a useful safety response. I also learned that for such a system to work well, the flow must be logical, fast, and relevant to the road situation. Working on this part improved my ability to think in terms of system interaction and functional design. Overall, this project helped me better understand how V2P can operate as a connected road safety system.

### Hessa – Focus on Vulnerable Pedestrians and User Needs
My role in this project was to contribute more towards the user-focused side of the V2P concept, especially in relation to vulnerable pedestrians. Although researching and understanding V2P was something done collectively by the team, I became more focused on how the system should respond to the needs of different pedestrian groups. Through this, I learned that V2P should not only be viewed as a communication technology, but also as a safety solution that must be designed around real human needs. I gained a better understanding of why vulnerable pedestrians such as children, the elderly, and people with disabilities may require additional protection in traffic environments. This supported the idea that our system should prioritise users who may face greater difficulty in crossing safely. I also realised that not all pedestrians experience the road in the same way, so a meaningful V2P system should reflect those differences. This experience taught me the importance of accessibility and inclusiveness in engineering design. Overall, it helped me see V2P as a human-centered transport safety solution.

### Hafiz – Research and Understanding of V2P Systems
My main contribution was in building my understanding of V2P systems and supporting the team’s discussion on how such systems can improve road safety. Since researching the V2P concept was a shared effort across the group, I also gained a broad understanding of how communication between pedestrians and vehicles can reduce accident risk. I learned that traditional safety measures often depend heavily on driver visibility and reaction time, whereas V2P adds another layer of awareness through direct communication. This made me appreciate why V2P is becoming an important concept in modern transport safety. Through this project, I understood that the value of V2P lies in its ability to support earlier detection and preventive action before a dangerous conflict happens. I also realised that communication-based safety systems can be especially useful in complex or fast-changing road environments. This experience improved my knowledge of how engineering and communication technologies can be applied to public safety. Overall, the project gave me a stronger understanding of why V2P is relevant and meaningful.

### Kelly – Practical Application and Safety Relevance
My main contribution was helping to connect the V2P concept to practical road safety applications. Like the rest of the team, I developed an understanding of the V2P concept through our shared research and project discussions. From this, I learned that the strength of V2P is not only in the communication itself, but in how that communication can support useful action from the driver. I focused more on understanding where such a system would be most relevant, such as zebra crossings, pedestrian-heavy areas, and locations where drivers may have limited time to react. This helped me appreciate that a V2P system must always be considered in terms of its practical safety purpose and not only its technical design. I also learned that one of the key advantages of V2P is its ability to improve reaction time before danger becomes obvious. This experience helped me better understand how engineering solutions become more impactful when they are linked to real-world applications. Overall, the project showed me how V2P can contribute to safer and more responsive transport systems.

## Repository Structure

/CEG3006_flowchart.png

/DecisionLog.md
- project development decisions

## Reference
De Ponte Müller, F., Munoz Diaz-Ropero, E., Sand, S., Böker, C., & Merk, L. (2022). Towards vision zero - V2X communication for active vulnerable road user protection. expert verlag. https://elib.dlr.de/190358/

Gelbal, S. Y., Cantas, M. R., Guvenc, B. A., Guvenc, L., Surnilla, G., & Zhang, H. (2023). Mobile safety application for pedestrians. https://arxiv.org/abs/2305.17575

Arena, F., Pau, G., & Severino, A. (2020). V2X communications applied to safety of pedestrians and vehicles. Journal of Sensor and Actuator Networks, 9(1), 3. https://doi.org/10.3390/jsan9010003
