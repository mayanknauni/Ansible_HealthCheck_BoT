# Ansible_HealthCheck_BoT#
#Raw Command Output from Ansible Delievered to CiscoWebEx Teams Rooms#

ChatOps : For Infra Engineers ( with sample Ansible Playbooks) 

Background
Imagine a situation wherein you need periodic output of a command ( running on your servers or network equipment), what do you do presently, login to the device and get it periodically or as and when needed, or run a script and check the outputs, what if the same output was delivered to you on your enterprise messaging platform. For this example, I will be using Cisco WebEx Teams and Ansible. 
The high-level architecture is below and quite self-explanatory. 


What is a ChatBot?
It is a software that conducts a conversation via over texts like a human being, it simulates a human interaction. For more information about WebEx Team ChatBot: -
https://developer.webex.com/docs/bots		
I am also training the chatbot to answer Level 1 Network Queries, using Dialogflow.
I am using Paramiko to connect to the devices and Cisco_Spark Module of Ansible to send the outputs to a Cisco WebEx Chat Room.

In future use cases, I would ask ChatBot for ad-hoc reports and it will trigger relevant jobs at the backend and deliver the results to the room. 
