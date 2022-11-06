1. What can happen if the robot is stuck and motors are active?
  * If the robot tries to go forward where it cannot, there is a high risk of the motors being damaged.
2.	What do you do if the robot is out of control?  
  * Stop the robot in emergency situations
     1. By issuing a stop command from Raspberry Pi  
   ```echo -ne "\xAD" > /dev/ttyUSB1```
   
     2. If the command doesn't work, pull out the battery in the following steps:  
        1. Release the Raspberry Pi components from the robot using the velcro sonnections and the associated cables.
        2. Turn the robot upside-down. 
        3. Remove the four screws circled; The screwdrivers will be above the whiteboard
in the Lab room.  
        4. Open the lid and pull out the battery carefully.
        5. Finally, put the battery back and make sure the screws and the lid are secure.
        6. Inform the lab assistant that you had to perform an emergency power off.
3. What is the role of the Refine task? 
   1. The Refine task gets the current location of the Robort by reading the information of the tags below the surface.
   2. Or the Refine task finds the position of a unknow victim, then forwards the infomation to the Report task.
4. How often does the Avoid task need to run?
   * The Avoid task need to run at least every 100-150ms.
5. Can tasks in the robot agent be preempted? 
   * No, robot agent code runs as a single Raspberry Pi process which means the
task scheduler in the robot agent has no possibility to preempt currently running tasks..
6. In which file(s) will solutions for lab 1 go? 
  * The file `scheduler.c`, which we write the code.
7. What is a metric? 
  * A metric is a system of measurement, used for performing standardised measurements of things in order to for example determine quality.
8. What metrics do you plan to use to show your WCET estimates are good enough? 
To ensure that the WCET estimates are good enough, we need many measurement points in a lot of differing situations, and to ensure that we catch the most extreme situations for each task.
9.  How do you plan to evaluate and measure the performance of the system as defined in Appendix F? 
In order to evaluate the required performance of the system, we need to be able to accurately measure the period of the avoid task, and time between RFID reading in the refine task and a message being sent within the report task. We also need to be able to measure how fast the robot can stop after recieving a stop message. This probably has to be measured physically, since we have to see the robot stop in order to stop the timer. It might also be sufficient to use normal software timers to find the time between when a stop command is received in the Mission task and the part where the lower-level command is sent to the motors to stop, if the time for the motors to physically stop is negligible. 
10.  When is the performance of the system satisfactory?
The performance of the system is satisfactory when we satisfy the requirements described in 3.2. So the avoid task should be run at least every 100-150 ms, the time between an RFID reading and a message being sent should be less than 1300 ms, and finally the robot must stop within 1300 ms if a stop command was received. 