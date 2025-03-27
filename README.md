<p align="center">
<img src="https://i.imgur.com/g4QNc8p.png" alt="osTicket logo"/>
</p>

<h1>Zendesk Support Administrator</h1>
Mastering the use of Zendesk for managing tickets and enterprise support.<br />

<!--
<h2>Video Demonstration</h2>

(In progress)
- ### [YouTube: Zendesk Support Administrator]()
-->

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

<p>
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

## So lets get started! :)
</p>


<h2>Agent Roles, Groups, Organizations, and User Tags</h2>

- Zendesk was built to communicate with millions of customers, so it is absolutely crucial to understand how we can manage our user accounts and their tickets without losing track of our processes.
- However, even when working with a smaller customer base, keeping scalability in mind is always a good tactic.
- We will cover the following topics:

1. Users/agents/custom agent roles
2. Groups
3. Organizations
4. User tags
5. Importing existing user databases (CSV file, Zendesk API)

## Users/agents
- Agents are just like end users and are classified as users.
- The role for end users is called <strong>end-user</strong>.
- The difference, however, can be found in the assigned role. The role defines what a user can or cannot do and end users, for example, do not possess the necessary rights to log in to the actual helpdesk environment.
- In Zendesk, <strong>users</strong> are also referred to as <strong>people</strong>. Both are equivalent terms. The same applies to the two terms <strong>end-users</strong> and <strong>customers</strong>.

- You can easily access the whole list of users by following these two steps:

1. Click on the Admin icon (gear symbol) located in Zendesk's sidebar.
2. then click "Go to Admin Center"
<br>
<p align="center">
<img src="https://imgur.com/jI9lfgN.png"/>
</p>

3. Click on "People" located in Zendesk's sidebar within the admin menu:

The types of roles available:
<p>Agent/Staff: Has the permissions in order to solve tickets.</p>
<p>Team leader: Allows more access to the Zendesk environment.</p>
<p>Advisor: Cannot solve any tickets. This role is supposed to enable the user to manage Zendesk's workflows. This entails the ability to create and edit automations, triggers, macros, views, and SLAs.</p>
<p>Administrator: Has additional permissions, allowing the user to customize and manage the Zendesk environment.</p>



## Creating Custom Agent role
We don't have the enterprise Editions, but Lets me tell you how its done.

1. Click on the Admin icon (gear symbol) located in Zendesk's sidebar.
2. Click on People located in the side menu of the admin menu.
3. Click on role:

The process of creating a custom role consists of naming and describing the role followed by defining the permissions

<br>
<p align="center">
<img src="https://imgur.com/s1Ry4qE.png"/>
</p>

Permissions are categorized under the following headings:

- Tickets
- People
- Help Center
- Tools
- Channels
- System

<br>
<p align="center">
Tickets
<img src="https://imgur.com/Ye600kD.png"/>
</p>

Only allowing the necessary permission for each role.For example, Tier 1 Techs, don't need permission to view or edit reports, as well as team leads don't need access to edit dynmic contents. Best to go with least privilege in order for that role to do their specific job and nothing more.

- Custom roles for our example:
- Tier 1
- Tier 2
- VIP
- Administrator


# Groups
Groups are only meant for agents and each agent must be at least in one group.

In our case, we have four types of support tickets:

- Tier 1 Support
- Tier 2 Support
- VIP Support
- Internal Support


