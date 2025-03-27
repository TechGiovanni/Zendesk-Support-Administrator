<p align="center">
<img src="https://i.imgur.com/g4QNc8p.png" alt="osTicket logo"/>
</p>

<h1>Zendesk Support Administrator</h1>
Mastering the use of Zendesk for managing tickets and enterprise support.<br />


<h2>Video Demonstration</h2>

(In progress)
- ### [YouTube: Zendesk Support Administrator]()


<h2>Environments and Technologies Used</h2>

- Zendesk
- Windows or Mac

<h2>Operating Systems Used </h2>

- Windows 11</b> (24H2)

<h2>List of Prerequisites</h2>

- Zendesk Free trial

<br>
<h2>For this LAB, our model company is itsolutions.</h2>

The scalability of your setup highly depends on the early planning phase. Before we can go through the process of such an evaluation, we need to establish a far-reaching scenario by creating a fictitious example company. For the sake of simplicity and not having to refer to the company as an example throughout this lab, we will call it itsolutions.

itsolutions is a Canadian tech company selling their own software online. They also offer some hardware created by a third-party in order to guarantee better compatibility and support.

Next to offering their software for individual purchase, customers can choose a yearly subscription allowing them access to the full range of software solutions. These customers are called "VIPs" and can purchase the hardware to a discounted price. As part of the subscription, VIP customers are supposed to receive faster responses from the support team.

itsolutions is still considered a start-up and cannot afford to provide customer-service in more than two languages (English and French), but are planning to offer support in more languages later on.


<h2>Desired setup</h2>
<br>
<p align="center">
<img src="https://imgur.com/K0Tt867.png"/>
</p>

We will have different channels of receiving tickets from regular and VIP users. Within our Ticket Views, we will divide and pool certain tickets together. The company only hires Bilingual Agents so we only group the tickets based on a tier system and a specific group for VIPs.
While VIP tickets will land directly in the corresponding VIP Support view, all non-VIP tickets will initially land in the Tier 1 view. Agents can then decide to push them into the Tier 2 view if the customer needs more technical help.

Our Ticketing Workflow:
1. A customer creates a ticket via one of our open channels.
2. Depending on the channel, tickets are assigned to one of the two escalation types.
3. If our customer is a VIP, we mark the ticket accordingly.
4. The ticket is now either in the Tier 1 or our VIP view.
5. An agent opens the ticket and decides whether to answer or push the ticket to the Tier 2 view for more complex support requests.
6.The customer receives a reply.
7. If the customer replies, the ticket shows up in the agent's own view. The agent receives an e-mail notification.
8. If the agent does not update the ticket with a given time frame, the ticket is moved back to its initial view.
9. Another agent can now pick up the ticket.

We will simply create Zendesk triggers and a custom ticket field as well as make use of automations. Using a macro called Push to Tier 2, allowing agents to push tickets to the Tier 2 view.

We need to set up the following:

Channels
Custom fields
Views
Business rules
Agent roles
SLAs
Macros
Global Zendesk settings / Security settings
Reporting
Zendesk apps

# <h2>Installation Steps</h2>

- Create a virtual network
- Create an address space on that virtual network
<br>
<p align="center">
<img src=".png"/>
</p>

- Create the virtual machine - Server 2022


<h2>The Zendesk environment</h2>















