# Decision Log



## Log 1 --- Mar 13th, 2026

### Trigger / Problem:
Initial project brainstorming. The team needed to define the target users and scope of the V2P safety application.


### Options / Alternatives:
1. General pedestrian safety system for all users.
2. System focused on vulnerable road users (disabled, elderly, students).
3. System including emergency vehicle communication. (Rejected)
4. System including speed limit zone notifications. (Rejected)


### Evaluation Criteria:
Relevance to V2P objective, system complexity, implementation feasibility, and alignment with project scope.


### Decision and Rationale:
The team decided to focus the application on vulnerable road users, such as handicapped users, elderly pedestrians, and students at crossings.

Two alternative features were discussed but rejected:
• Emergency vehicle notification – rejected because it mainly involves Vehicle-to-Vehicle (V2V) communication rather than V2P.
• Speed limit zone warning – rejected because it would require Vehicle-to-Infrastructure (V2I) integration with traffic systems, which is outside the project scope.

This decision keeps the system aligned with the V2P safety objective while maintaining manageable system complexity.


### Team Member
Entire team





## Log 2 --- 24th March, 2026

Since the assignment specifically requires a V2P application, it is more appropriate to implement a pedestrain-vehicle system rather than a pedestrian-traffic-vehicle system.

System Architecture to be used:
- Pedestrian side
- Pedestrian-Vehicle side
- Vehicle side
- In vehicle warning subsystem

Rejection
- BLE due to its short range, unpredictable latency, possible unstable connection

Initial decision:
- Only use either PC5 or Uu only
- Later decided to hybrid (use both PC5 and Uu)
