# Decision Log



## Log 1 — 13 Mar 2026

### Trigger / Problem
Initial project brainstorming. The team needed to define the target users of the V2P safety application.

### Options / Alternatives
- General pedestrian safety system for all users
- System focused on vulnerable road users

### Evaluation Criteria
Relevance to V2P objective, clarity of target users, project scope

### Decision and Rationale
The team decided to focus on vulnerable road users instead of all pedestrians. This gave the project a clearer scope and stronger justification.

### AI Usage
AI was used for idea generation, but the team decided the final focus.



## Log 2 — 13 Mar 2026

### Trigger / Problem
The team needed to define which vulnerable users should be prioritized.

### Options / Alternatives
- General vulnerable road users
- Disabled users, elderly pedestrians, and students at crossings

### Evaluation Criteria
User relevance, safety impact, suitability for V2P use case

### Decision and Rationale
The team decided to prioritize disabled users, elderly pedestrians, and students, as these groups are more vulnerable and align well with the project objective.

### AI Usage
AI helped brainstorm possible target groups, but the final grouping was chosen by the team.



## Log 3 — 13 Mar 2026

### Trigger / Problem
The team discussed whether to include emergency vehicle communication in the system.

### Options / Alternatives
- Include emergency vehicle notification
- Exclude emergency vehicle notification

### Evaluation Criteria
Alignment with V2P scope, technical relevance

### Decision and Rationale
The team rejected emergency vehicle notification because it mainly relates to Vehicle-to-Vehicle (V2V) communication rather than V2P.

### AI Usage
AI suggestions were reviewed, but the team rejected this feature based on scope.



## Log 4 — 14 Mar 2026

### Trigger / Problem
The team discussed whether to include speed limit zone notifications.

### Options / Alternatives
- Include speed limit zone warning
- Exclude speed limit zone warning

### Evaluation Criteria
System complexity, required infrastructure, alignment with project scope

### Decision and Rationale
The team rejected speed limit zone warning because it would require Vehicle-to-Infrastructure (V2I) integration with traffic systems, which was considered outside project scope.

### AI Usage
AI suggested related ideas, but the team decided not to include them.



## Log 5 — 24 Mar 2026

### Trigger / Problem
The assignment specifically required a V2P application, so the team reviewed the communication structure.

### Options / Alternatives
- Pedestrian–traffic–vehicle system
- Direct pedestrian–vehicle system

### Evaluation Criteria
Fit to assignment requirement, simplicity, relevance to V2P

### Decision and Rationale
The team chose a direct pedestrian–vehicle system because it is more appropriate for a V2P application than a pedestrian–traffic–vehicle architecture.

### AI Usage
AI discussion helped compare architectures, but the decision was made by the team.



## Log 6 — 24 Mar 2026

### Trigger / Problem
The team needed to define the main architecture blocks of the proposed system.

### Options / Alternatives
Different ways of dividing the system architecture

### Evaluation Criteria
System clarity, modularity, ease of explanation

### Decision and Rationale
The team structured the design into the following subsystems:
- Pedestrian side
- Pedestrian–Vehicle communication side
- Vehicle side
- In-vehicle warning subsystem

This made the system easier to explain and document.

### AI Usage
AI helped refine subsystem wording and organization



## Log 7 — 24 Mar 2026

### Trigger / Problem
The team considered using BLE as the communication method.

### Options / Alternatives
- BLE
- C-V2X-based communication

### Evaluation Criteria
Range, latency, connection stability, suitability for safety warnings

### Decision and Rationale
The team rejected BLE because of its shorter range, less predictable latency, and possible connection instability compared with the needs of the proposed system.

### AI Usage
AI provided comparisons between BLE and C-V2X, but the final rejection was based on project needs.



## Log 8 — 24 Mar 2026

### Trigger / Problem
The team needed to decide whether to use only one C-V2X interface or combine both.

### Options / Alternatives
- Use only PC5
- Use only Uu
- Use both PC5 and Uu

### Evaluation Criteria
Support for live safety communication, backend support, architectural completeness

### Decision and Rationale
The team first considered using only PC5 or only Uu, but later decided to use a hybrid approach with both PC5 and Uu. This allowed separation between live safety communication and backend/update functions.

### AI Usage
AI helped explain the differences between PC5 and Uu, but the final architecture choice was made by the team.



## Log 9 — 25 Mar 2026

### Trigger / Problem
The team needed to improve project documentation and ensure the written description matched the finalized concept.

### Options / Alternatives
- Keep earlier description
- Update brief description and flowchart to match the refined design

### Evaluation Criteria
Consistency, clarity, quality of documentation

### Decision and Rationale
The team updated the brief description, system architecture flowchart, and early/final system sketches so that the documentation reflected the final design more accurately.

### AI Usage
AI helped refine wording and flowchart structure, but team review was needed to keep the content aligned with the actual design.



## Log 10 — 25 Mar 2026

### Trigger / Problem
The team needed to decide how warnings should be presented to the driver.

### Options / Alternatives
- Visual warning
- Audio warning
- Combined visual and audio warning

### Evaluation Criteria
Driver distraction, clarity of alert, suitability for safety application

### Decision and Rationale
The team finalized the use of audio warning on the vehicle side to avoid distracting the driver with visual alerts.

### AI Usage
AI suggested different warning approaches, but the final decision was made based on usability and safety considerations.
