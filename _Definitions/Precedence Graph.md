1. Place every transaction in a circle. 
2. Checking the schedule, if a transaction x *reads* after another transaction y *writes*, draw an arrow from $t_y$ to $t_x$. Label with the variable read. 
3. Repeat for every transaction combination. 

![[Screenshot 2023-11-17 at 1.32.07 PM.png]]

Analysis of graph:
- If there is no cycle made up of one variable (cycle of just X operations), it is serializable. 