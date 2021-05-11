# tmux quick hits
If you lose console on a tmux app, use `send-keys` option:
   - Example:
       - I started a bedrock server on tmux, but lost console output.  I need to send the shutdown command but have it gracefully save and close ports.  
       - Solution:  
         ```
         tmux send-keys -t bedrock:0.0 stop Enter
         ```
         - This sends the `stop <Enter>` command to the console in tmux
       
----

# Cousin's Server Contests
## Super Happy Fun Time Jolly Bee Family Server

### Checkilist
1. Lock server 1 hour prior to contest
1. Minimize Digging if scavenger hunt
1. Add barriers over home and basement
   ```
   give spaceshiptrp barrier 256
   ```
1. Create Contest wall and add a bell
1. Add Date of Contest in sign on plaque at Town Square
1. Copy rules of contest to a plaque in the town square
1. Lock up the enchanted room outside Sophia's house
1. Set time to 1000
   ```
   time set 1000
   ```

   
#### 2021 April 24
* 10AM Pacific
* Lock Server at 9AM Pacific
* For first contest, set to always daytime
   ```
   /gamerule doDaylightCycle false
   ```
* Find spot within 1000 block radius from Llama House
* No digging -- Possibly under water?
* Should we turn off coordinates?
* Upon completion of the contest, open enchanted room again
* Set day cycle to continue
   ```
   /gamerule doDayLightCycle true
   ```

##### Announced Rules:
* This will be simple, straight up scavenger hunt
* No digging required
* Look for something that Uncle Jay made it will be very obvious
* Somewhere within a 1000 block radius from Llama House
* First one to find it keeps it
* Write your name in the town square Plaque as the winner for contest date - winner must also add time
* Send a Test to Uncle Jay to say you found it and tell him what it is.
* If all the steps are followed and it is complete, Uncle Jay will send text to the entire group stating the prize has been found.
* Player gets to keep what they found
* Teams are encouraged.  If folks work as a team, all team members will get the prize
---
# TODO
* Create super sword
* Create throwable ninja stars
* Create pickaxe that can break anything and everything try to break `barrier` blocks
* Make floating sign for Town Square
  - Add a Google Pin from the top
  - Make it very large so it can be seen from everywhere 
