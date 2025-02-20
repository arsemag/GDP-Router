Class Definitions
Router
This class defines the router logic, including the management of forwarding tables, route aggregation, and handling of different message types.

Attributes:
relations: Stores relationship mappings with neighboring routers (e.g., customer, peer).
sockets: Contains the UDP sockets for communication.
ports: Holds the port mappings for each neighbor.
forwarding_table: The list of network routes managed by the router.
Methods:
__init__(self, asn, connections): Initializes the router with its Autonomous System Number (ASN) and connections.

our_addr(self, dst): Returns the router's IP address based on the destination.

send(self, network, message): Sends a message to a specific network.

run(self): Starts the router and begins processing incoming messages.

process_message(self, message, source): Determines the action to take based on the message type.

handle_data_message(self, data, source): Processes incoming data messages and forwards them if necessary.

update_forwarding_table(self, message, source): Updates the forwarding table with new routing information.

now_aggregate(self, routes): Aggregates routes based on the network mask and routing information. 
The helper route_sort_key() was used within this method which gets return the the route
to be used during the aggregation. 

send_updates(self, route, sender): Sends route updates to neighbors according to their relationship type.

drop_data(self, data): Drops data if no route is available to the destination.

send_withdraw(self, remove_list, sender): Sends a withdraw message to its neighbors


******** HELPERS *******
ip_to_int() : changes the IP to an int

int_to_ip(): changes an int to an IP address

make_copy(): makes copies of route announcements 

find_the_best_route(self, dst): Finds the best route for a given destination of a data message.

ip_to_binary(): function converts IP addresses into binary format, which is essential for bitwise operations

netmask_to_prefix(): function calculates the prefix length of a netmask by counting the number of '1' bits 
in the binary representation of the netmask.

ip_in_network(): method is another key component that determines if a given IP address belongs to a 
particular network


### TESTING ### 
Throughout the development process, I used print statements and broke down the code into smaller sections to
pinpoint where things were going wrong. I would test different scenarios, remove certain conditions, and change 
the code to make sure everything worked as expected. This helped me catch and fix issues step by step, making 
sure the final solution was both stable and accurate.