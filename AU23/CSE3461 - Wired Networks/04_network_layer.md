# Planes and Overview




# Subnets
Any time we leave a router interface, we are in a new subnet. 
# CIDR
Classless interDomain Routing. 

# IP addresses tutorial
request from ip
divide nets by bit
# DHCP 
Application layer model. Used to dynamically assign IP Addr

Steps:
1. Computer broadcasts on 0.0.0.0:67 that it wants an ip. Chooses random transaction_ID
2. All DHCP servers reply with offer of ip and returns transaction_ID. Sends over 255.255.255.255:68
3. Computer chooses one and creates new message with transaction_id+1, 0.0.0.0:67, sends. 
4. DHCP server replies with confirmation. It may offer same ip to many but the first to accept gets it. 

# NAT
Network Address translation. Translates local nonroutable IP to another address. 

Holds a table that maps WAN side address to LAN side address. Any new unknown address gets a new mappable address and is stored. A WAN side address is an adapter. 
