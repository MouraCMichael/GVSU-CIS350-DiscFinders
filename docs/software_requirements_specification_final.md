# Overview 
The purpose of this document is to outline the features of the DiscFinders Application. The document provides the scope of the project for the developers and outlines the framework for its development. This document is intended for project team members and the instructor in CIS 350 at GVSU.
 
# Software Requirements
This section contains both the functional and non-functional requirements of this project. Each requirement is located under a specific category in either the functional of non-functional heading to which it applies. 
<br/><br/>
## Functional Requirements 

### RFID Communication 
| ID | Requirement | Test Cases |
| :------------- | :---------- | :----------: | 
| FR1  |  The device shall transmit data via RFID signal at 13.56Mhz               | TC7, TC8 | 
| FR2  |  The device shall receive data via RFID signal of 13.56Mhz             			| TC7, TC8 | 
| FR3  |  The device shall communicate to all NFC Data Exchange Formatted tags  		 | TC7, TC8 | 
| FR4  |  The device shall communicate with multiple NDEF tags                  			| TC7, TC8 | 
| FR5  |  The device shall communicate up to 10cm                               			| TC7, TC8 | 

### Display
| ID | Requirement | Test Cases |
| :------------- | :---------- | :----------: | 
| FR6  |  The device shall display the tag name for every successfully read attempt          		| TC1, TC9, TC10 |
| FR7  |  The device shall display an error message for every unsuccessful read attempt  		    | TC1, TC9, TC10 |
| FR8  |  The device shall display a message when data has been successfully written to tag  	 | TC1, TC9, TC10 |
| FR9  |  The device shall display an error message for every unsuccessful write to tag      		| TC1, TC9, TC10 |
| FR10 |  The display shall display when it is actively searching for the tag                		| TC1, TC9, TC10 |

### Interactive Switches
| ID | Requirement | Test Cases |
| :------------- | :---------- | :----------: | 
| FR11 |  A switch shall power on and power off the device                               			 | TBD |
| FR12 |  A switch shall allow the user to toggle between reading and writing to a tag   		  | TBD |
| FR13 |  A switch shall initiate the reading process                                   	 		 | TC2 |
| FR14 |  A switch shall initiate the writing process                                   			  | TBD |
| FR15 |  A switch shall initiate a soft reset of the device                             			 | TBD |

<br/><br/>

## Non-Functional Requirements 

### RFID Communication 
| ID | Requirement | Test Cases |
| :------------- | :---------- | :----------: | 
| NFR1 | The device shall reliably read data from tag          				 | TBD | 
| NFR2 | The device shall reliably write data to tag           				 | TBD | 
| NFR3 | The device shall easily switch between RFID signals   				 | TBD | 
| NFR4 | The device shall not transmit with audible noise      				 | TBD |
| NFR5 | The device shall easily pair with the RFID tag        				 | TBD |

### Display 
| ID | Requirement | Test Cases |
| :------------- | :---------- | :----------: | 
| NFR6   |  The display shall be easy to read                                                         		| TBD |
| NFR7   |  The display shall noticeably change when near the device                                  		| TBD |
| NFR8   |  The device shall provide feedback to the user about the RFID tag when searching  	          | TBD |
| NFR9   |  The device shall provide accurate character feedback prior to writing data                	 | TC3, TC4, TC5, TC6 |
| NFR10 |  The device shall have intuitive screen layouts                                            		 | TBD |

### Interactive Switches 
| ID | Requirement | Test Cases |
| :-------------: | :----------: | :----------: | 
| NFR1 |  The power switch shall be in a location easy to press       				 | TBD |
| NFR2 |  The soft reset switch shall be in a location easy to press  				 | TBD |
| NFR3 |  The switches shall not interfere with holding the device    			  | TBD |
| NFR4 |  The switches must not interfere with reading the display    			  | TBD |
| NFR5 |  The switch layout must be intuitive                         			 	| TBD |



<br/><br/>

# Test Specifications

This section outlines the unit, integration, and system test =s conducted on this project.  Each test reflects some aspect of the functional and non-functional requirements listed in the previous section.  A description of each test is provided along with the test input, expected output, actual output and whether or not the element in question passes the test.


## Unit tests - Unit tests check tiny bits of functionality (function inputs/outputs, etc.) 
| ID | Description | Steps | Input Values | Expected Output | Actual Output | Pass/Fail | Requirement Link |
| :-------------: | :----------: | :----------: | :----------: | :----------: | :----------: | :----------: | :----------: | 
| TC1   | Check LCD character display function | Send a set of parameters and check that the message is displayed on the LCD | 1, ST77XX_WHITE, 36, 57,   "TEST_1!" | "TEST_1!"  | "TEST_1!" | Pass | FR6, FR7, FR8, FR9, FR10 | 

## Integration tests - Integration tests check for errors when you bring together two or more modules 
| ID | Description | Steps | Input Values | Expected Output | Actual Output | Pass/Fail | Requirement Link |
| :-------------: | :----------: | :----------: | :----------: | :----------: | :----------: | :----------: | :----------: | 
| TC2   | The ‘B’ button on the LCD Shield initiates the RFID shield search process in appropriate state. | Highlight “Search For Disc” on Home Screen | Button Inputs | Searching Screen Appears | Searching Screen Appears | Pass| FR13 | 
| TC3   | The “Up” button increments the ACSii value character displayed on the LCD        | Select “Change Disc Name” > press up on the joystick       | Button Inputs | ‘A’ , ‘B’, ‘C’,...    | ‘A’ , ‘B’, ‘C’,... ‘Z’  | Pass | NFR4 |
| TC4   | The “Down” button decrements the ACSii value character displayed on the LCD  | Select “Change Disc Name” > press down on the joystick | Button Inputs | ‘@’ , ‘?’, ‘>’,...   | ‘@’ , ‘?’, ‘>’,...      | Pass | NFR4 |
| TC5   | The “Left” button removes the current character on the LCD  | Select “Change Disc Name” > press Right on the joystick 3 times then press left on the joystick 2 times   | Button Inputs |  ‘A’ | ‘A’ | Pass | NFR4 | 
| TC6   | The “Right” button increments the LCD cursor to the next character location       | Select “Change Disc Name” > press Right on the joystick 3 times | Button Inputs | “AAAA” | “AAAA”  | Pass | NFR4 | 


## System tests - System tests check the system as a whole once everything is put together 
| ID | Description | Steps | Input Values | Expected Output | Actual Output | Pass/Fail | Requirement Link |
| :-------------: | :----------: | :----------: | :----------: | :----------: | :----------: | :----------: | :----------: | 
| TC7   |  RFID initialization successful                 | Connect all components –  power on | N/A | “RFID Init Successful”       | “RFID Init Successful”      | Pass  | FR1, FR2, FR3, FR4, FR5  |
| TC8   |  RFID shield initialization unsuccessful | Remove RFID shield – power on          | N/A | “RFID Init Unsuccessful”  | “RFID Init Unsuccessful” | Pass  | FR1, FR2, FR3, FR4, FR5  | 
| TC9   |  LCD Shield initialization successful      | Connect all components –  power on  | N/A | “LCD Init Successful”        | “LCD Init Successful”       | Pass  | FR6, FR7, FR8, FR9, FR10|    
| TC10   | LCD Shield initialization unsuccessful   | Remove LCD shield – power on          | N/A | “LCD Init Unsuccessful”   | “LCD Init Unsuccessful”  | Pass  | FR6, FR7, FR8, FR9, FR10 | 

<br/><br/>

# Software Artifacts

This section provides links to all of the software artifacts and project documentation.  The artifacts and documentation listed below afford all associated parties transparency into the project.  This section can be extremely important for research and development purposes, and sheds insight into reasonable timeline projections for future projects with similar system requirements.       

* [Project Proposal]( https://github.com/MouraCMichael/GVSU-CIS350-DiscFinders/blob/master/docs/Proposal.md)

* [Research and Documentation]( https://github.com/MouraCMichael/GVSU-CIS350-DiscFinders/blob/master/artifacts/Research%20and%20Documentation.pdf)

* [Program Library Details]( https://github.com/MouraCMichael/GVSU-CIS350-DiscFinders/blob/master/artifacts/Program%20Library%20Details.pdf)

* [Arduino Library Install Guide]( https://github.com/MouraCMichael/GVSU-CIS350-DiscFinders/blob/master/artifacts/RFID%20Shield%20Library%20Install%20Directions.pdf)

* [Design Proposals 1]( https://github.com/MouraCMichael/GVSU-CIS350-DiscFinders/blob/master/artifacts/Design%20Proposal%201.pdf)

* [Project Timeline](https://github.com/MouraCMichael/GVSU-CIS350-DiscFinders/blob/master/docs/Gantt%20Chart.pdf)

* [Assigned Tasks Overview]( https://github.com/MouraCMichael/GVSU-CIS350-DiscFinders/blob/master/docs/Tasks.md)

* [SRS Midterm]( https://github.com/MouraCMichael/GVSU-CIS350-DiscFinders/blob/master/docs/software_requirements_specification.md )

* [Use Case Diagrams]( https://github.com/MouraCMichael/GVSU-CIS350-DiscFinders/tree/master/artifacts )

* [Midterm Presentation]( https://github.com/MouraCMichael/GVSU-CIS350-DiscFinders/blob/master/docs/Midterm%20Presentation.pdf )

* [State Machine Final]( https://github.com/MouraCMichael/GVSU-CIS350-DiscFinders/blob/master/docs/state_machine_final.pdf )

* [Final Presentation](https://github.com/MouraCMichael/GVSU-CIS350-DiscFinders/blob/master/docs/DiscFinders%20Final%20Presentation.pdf)

* [Code Revisions]( https://github.com/MouraCMichael/GVSU-CIS350-DiscFinders/tree/master/CodeRevisions)

* [Meeting Minutes]( https://github.com/MouraCMichael/GVSU-CIS350-DiscFinders/tree/master/meetings )










