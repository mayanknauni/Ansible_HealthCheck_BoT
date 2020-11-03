# Ansible: Cisco APIC Health Check with Cisco WebEx BoT Integration

Raw Command Output from Ansible Delivered to Cisco WebEx Teams Rooms

# Objective
Imagine a situation wherein you need periodic output of a command ( running on your servers or network equipment), what do you do presently, login to the device and get it periodically or as and when needed, or run a script and check the outputs, what if the same output was delivered to you on your enterprise messaging platform. For this example, I will be using Cisco ACI, Cisco WebEx Teams and Ansible Tower. The same script can be extended to majority of Cisco devices. 

# What is a Chat Bot?
It is a software that conducts a conversation via over texts like a human being, it simulates a human interaction. For more information about WebEx Team ChatBot: -
https://developer.webex.com/docs/bots
I am also training the chatbot to answer Level 1 Network Queries, using Dialogflow.
I am using Paramiko to connect to the devices and Cisco_Spark Module of Ansible to send the outputs to a Cisco WebEx Chat Room.

# Requirements
To use this code, you will need:
•	Ansible Tower or Ansible (scheduling options are only available with Ansible Tower)
•	Cisco WebEx Teams Account and Room ID
•	Paramiko library 
•	Cisco_Spark Module on Ansible 
•	Cisco Devices (Router / Switches / APIC etc. )

# Using the Playbook
1.	Download the file ACI_Controller_Health.yml
2.	Modify the host name to point to your device i.e. router / switch / apic etc 
3.	Modify the below line of code to execute the command as per your device: -

 raw: "show controller" # Any Command that you wish to execute \
Example commands are 
* “show process cpu history” * 
* “show logg | i keyword” *

4.	Login to  https://developer.webex.com/
5.	Create a Bot 
6.	Add this bot to the room where you wish to send the messages
7.	Populate the below mentioned information from the webex developer portal to the file ACI_Controller_Health.yml

connection: local
gather_facts: False
tasks:
\- name: Sending message to room # Sending the Command output to the room, you can the RoomID and Personal Token from WebEx Developer Portal \
cisco_spark: \
recipient_type: roomId \
recipient_id: {{roomID}} #Room ID of the room you wish to send the message to \
message_type: text \
personal_token: {{token}} #Token from the bot you created and was generated during the process.

8.	The scripts can be executed as standalone from ansible by executing ansible-playbook ACI_Controller_Health.yml -v 
9.	Once the step 8 is successful, the same script can be scheduled on Ansible Tower for periodic delivery to chat room.

# Lab Topology:
 
 ![alt text](https://github.com/mayanknauni/Ansible_HealthCheck_BoT/blob/master/ChatBot2.0.jpg?raw=true)


[![published](https://static.production.devnetcloud.com/codeexchange/assets/images/devnet-published.svg)](https://developer.cisco.com/codeexchange/github/repo/mayanknauni/Ansible_HealthCheck_BoT)
