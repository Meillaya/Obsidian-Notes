# Assignment 2

By: 
Nathan Agbomedarho - agbomedn - 400081762 - Q1, Q2, Q5
Deep Vikram Liya – liyad – 400257406 – Q3, Q4, Q6


## Question 1

| Requirement ID | Requirement Name                    | Requirement Description                                                                                              | Fit Criteria         |
| -------------- | ----------------------------------- | -------------------------------------------------------------------------------------------------------------------- | -------------------- |
| FR-1           | System Gameplay                     | The system will allow a user to play the game                                                                      | N/A                  |
| FR-2           | Airspace Selection                  | The system must allow the player to choose an airspace                                                             | N/A                  |
| FR-3           | Map Display                         | The system will display a map of the airspace                                                                      | N/A                  |
| FR-4           | Separation Rule Violation Detection | The system must detect a violation of the separation rule and should lead to a collision and the game ends         | N/A                  |
| FR-5           | Top-Down View Display               | The system must display a top-down view of all active flights in the airspace                                      | N/A                  |
| FR-6           | Entry-Point Restriction             | The system must not allow airspaces to have less than three entry and three exit points                            | N/A                  |
| FR-7           | Waypoint Restriction                | The system must not allow airspaces to have less than 10 waypoints                                                 | N/A                  |
| FR-8           | Unsaved Progress Detection          | The system will warn the player about unsaved progress if the player attempts to end the game with unsaved changes | N/A                  |
| NFR-1          | **Precision**: Response Time                        | The system must respond to user commands within 2ms.                                                               | Refer to Question 2. |
| NFR-2          | **Usability**: Intuitive & Accessible GUI              | The GUI of the game must be designed in a way that is intuitively usable and easily interpretable                  | Refer to Question 2. |

## Question 2

***NFR-1***

Requirement Name:
**Precision**: Response time

Requirement: Description: 
The system must respond to user commands within 2ms.

Fit Criteria:
- The game will be designed in such a way to prioritize system responsiveness, efficiency & speed.
- The game will be developed with an engine that allows for the game system to respond to player inputs near instantaneously.

Fit Criterion Justification:
Fit criteria are important to qualify a non-functional requirement as they qualify
A long response time will ruin any players' experience of the game, resulting in dissatisfaction and frustration, as such it is imperative that the central system of the game is programmed with an emphasis on speed and responsiveness to user interaction, as this will greatly enhance the players' experience & enjoyment of the game.

***NFR-2***

Requirement Name:
**Usability**: Intuitive & Accessible GUI

Requirement: Description: 
The GUI of the game must be designed in a way that is intuitively usable and easily interpretable

Fit Criteria:
- The GUI of the game will display all aspects of the game(e.g. airspace, flights, flight routes, waypoints, aircraft characteristics, etc.) in an organized manner.
- The game will release with an option to customize flight specific characteristics: colors/patterns to flight routes, icon for flights to display information(air speed, weight, crew/passenger count)

Fit Criterion Justification:
The GUI of the game is responsible for displaying all aspects of the game such as the airspace, flights, flight routes, waypoints, aircraft characteristics and others. The player will need to watch many things, as such it is important that the user interface is clean, usable, accessible and organized to allow interactions between the player and the game to be seamless and intuitive. The better designed the GUI is the better the gameplay experience of the player will be.


## Question 3
![[q3.drawio.png]]
## Question 4
![[q4.png]]
## Question 5

Sequence Diagram: 
Below displays information flow through a typical playthrough.

![[sequence diagram.drawio.png]]



## Question 6