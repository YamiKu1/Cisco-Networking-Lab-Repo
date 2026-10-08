# Cisco-Networking-Lab-Repo
## Step 1 — Install Cisco Packet Tracer

Download and install Cisco Packet Tracer

## Step 2 — Create the basic topology

Drag these devices into the workspace:

Network devices:

1 router

1 switch

End devices:

6 PCs

Router: 2911
Switch: 2960

## Step 3 — Connect everything

Use Copper Straight-Through cables.
Connect: 

Router G0/0 to Switch G0/1

Switch F0/1 → PC1

Switch F0/2 → PC2

Switch F0/3 → PC3

Switch F0/4 → PC4

Switch F0/5 → PC5

Switch F0/6 → PC6

Go into CLI for router and switch, use commands "enable" and "configure terminal" to change hostname to R1 for router and SW1 for switch.

## Step 4 — Save your project

Create a folder on your computer:
IT-Infrastructure-Lab

Inside:

Cisco-Network-Lab

Save your Packet Tracer file as:

CCNA-Networking-Lab.pkt

## Step 5 — Assign the departments

IT:

PC1 & PC2

HR:

PC3 & PC4

Sales:

PC5 & PC6


## Step 6 — Configure the switch
Click your switch.

Go to:

CLI

You'll see something like:

Switch>

Enter:

enable (shortcut "en")

Then:

configure terminal (shortcut "conf t")

Now create the VLANs:

vlan 10

then change its name:

name IT

exit

repeat for other VLANs:

vlan 20

name HR

exit

vlan 30

name SALES

exit

vlan 40

name MANAGEMENT

exit

You've just created four VLANs.

## Step 7 — Assign PCs to VLANs

PC1 and PC2 belong to IT.

Configure:

interface range fastEthernet 0/1-2 (shortcut "int range f0/1 - 2)

switchport mode access (shortcut "sw mode ac")

switchport access vlan 10 (shortcut "sw ac vlan 10")

exit

PC3 and PC4:

interface range fastEthernet 0/3-4 (shortcut "int range f0/3 - 4)

switchport mode access (shortcut "sw mode ac")

switchport access vlan 20 (shortcut "sw ac vlan 20")

exit

PC5 and PC6:

interface range fastEthernet 0/5-6 (shortcut "int range f0/5 - 6)

switchport mode access (shortcut "sw mode ac")

switchport access vlan 30 (shortcut "sw ac vlan 30")

exit

Now your switch knows which department each PC belongs to.

## Step 8 — Verify your VLANs

Type:

do show vlan brief (shortcut "do sh vlan br")

You should see something similar to:

VLAN   Name          Ports

10     IT            Fa0/1, Fa0/2

20     HR            Fa0/3, Fa0/4

30     SALES         Fa0/5, Fa0/6

40     MANAGEMENT

Take a screenshot.

## Step 9 — Configure PC IP addresses

Now we're configuring the actual PC, not the switch.

Click:

PC1 → Desktop → IP Configuration

You'll see:

IP Configuration

IPv4 Address:
Subnet Mask:
Default Gateway:
DNS Server:

Enter:

PC1

IPv4 Address:

192.168.0.10

Subnet Mask:

255.255.255.192

That's /26.

Default Gateway:

192.168.0.1

Leave DNS blank for now.

So PC1 is:

PC1
IP:       192.168.0.10
Mask:     255.255.255.192 (/26)
Gateway:  192.168.0.1
VLAN:     10

## Step 10 — Configure PC2

Click:

PC2 → Desktop → IP Configuration

Enter:

IP Address:       192.168.0.11
Subnet Mask:      255.255.255.192
Default Gateway:  192.168.0.1

So:

PC2
IP:       192.168.0.11
Mask:     /26
Gateway:  192.168.0.1
VLAN:     10

Notice that PC1 and PC2 are in the same subnet:

192.168.0.0/26

## Step 11 — Configure PC3

Now we're moving to VLAN 20.

VLAN 20's network is:

192.168.0.64/26

The usable addresses are:

192.168.0.65
through
192.168.0.126

The first usable address will be our gateway:

192.168.0.65

So PC3 gets:

IP Address:       192.168.0.70
Subnet Mask:      255.255.255.192
Default Gateway:  192.168.0.65

Therefore:

PC3
IP:       192.168.0.70
Mask:     /26
Gateway:  192.168.0.65
VLAN:     20

## Step 12 — Configure PC4

Use:

IP Address:       192.168.0.71
Subnet Mask:      255.255.255.192
Default Gateway:  192.168.0.65

So:

PC4
IP:       192.168.0.71
Mask:     /26
Gateway:  192.168.0.65
VLAN:     20

## Step 13 — Configure PC5

VLAN 30 is:

192.168.0.128/26

Usable:

192.168.0.129 – 192.168.0.190

Gateway:

192.168.0.129

PC5:

IP Address:       192.168.0.140
Subnet Mask:      255.255.255.192
Default Gateway:  192.168.0.129


## Step 14 — Configure PC6

PC6:

IP Address:       192.168.0.141
Subnet Mask:      255.255.255.192
Default Gateway:  192.168.0.129
