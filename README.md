<h1>Open Shortest Path First (OSPF) Configuration and Troubleshooting</h1>

<h2>Objective</h2>
Develop and demonstrate practical expertise in configuring, optimizing, and troubleshooting Open Shortest Path First (OSPF) routing within enterprise network environments. Build hands-on experience with single-area OSPF, router ID, network advertisements, area assignment, neighbor adjacencies, route summarization, and OSPF authentication. Troubleshoot common routing issues by analyzing neighbor relationships, routing tables, LSAs, interface states, and OSPF metrics to identify and resolve connectivity and convergence problems. Strengthen network engineering skills through structured lab scenarios using Cisco IOS and network simulation platforms such as Packet Tracer

<h2>Program</h2>
<p align="center">
<img src="https://i.imgur.com/HTYmkcs.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
Within this diagram of a small network, we want to create dynamic routes using Open Shortest Path First (OSPF) instead of static routes to lessen the complication of troubleshooting when an interface or subnet goes down, and less overhead and resource intensive on the Cisco routers.

Let’s begin with having the interfaces on each router already configured with its respective IP address and network mask and see what happens when we ping from one router to another.

<p align="center">
<img src="https://i.imgur.com/xqGJhDN.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

From this router, we can’t communicate with another network outside this router. Why is that? Because there are no routes configured to be able to communicate with other subnets outside of this router’s network.
<p align="center">
<img src="https://i.imgur.com/hemydlK.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
So how can we have this router in its own subnet communicate with other subnets? Besides configuring static routes to prevent human error and lessen troubleshooting complications later, we can configure Open Shortest Path First as a dynamic routing protocol.
Let’s say we want to configure this router to communicate with the 192.168.10.0 network. Let’s configure that on R2 as it is configured with a 192.168.20.0 and 192.168.30.0 ip address per interface.
<p align="center">
<img src="https://i.imgur.com/Rx8SWp8.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
Now let’s ping an address from the 192.168.0.0 network.
<p align="center">
<img src="https://i.imgur.com/XXIdCps.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
It seems that communication can’t be yet reached. Why is that? Because the router with the address 192.168.0.1 hasn’t been configured with OSPF. So, let’s do that on that router as well as the remaining router with OSPF. Note that when configuring OSPF, we must include all the network subnets for the dynamic routing to work and allow network communication.
<p align="center">
<img src="https://i.imgur.com/BTeJS6N.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
On R1, we can see that all of the network subnets have been included and configured with OSPF and a message below popped up to show the process from LOADING to FULL as OSPF is being initiated and ready to use.
Now let’s ping 192.168.10.1 again from R2.
<p align="center">
<img src="https://i.imgur.com/nxqMf6K.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
It worked because OSPF has been properly configured on each of the routers for proper communication for dynamic routing.
Let’s also check the IP route table to view the configuration.
<p align="center">
<img src="https://i.imgur.com/fNJYxYp.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
As we can see, OSPF is included on the IP Route table and is configured with the included network subnets for dynamic routing to work.
