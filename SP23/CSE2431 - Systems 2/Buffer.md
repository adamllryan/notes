>A producer adds data into the buffer
>A consumer removes data from the buffer
>*in* and *out* are the indices of BUFFER

To add: Add item to (in+1)%SIZE and set index
___
	init:
		```in = 0
		out = 0```
	Add an item: 
		```in = 1
		out = 0```
	Remove an item:
		```in = 1
		out = 1```
	Operations:
		```in +1%SIZE
		out+1%SIZE```
	Parameters:
		```BUFFER is empty if in == out
		is full if in+1%SIZE==out```
___
Bounded buffer has full detection


