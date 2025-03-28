<p align="center">
<img src="https://i.imgur.com/g4QNc8p.png" alt="osTicket logo"/>
</p>

# Zendesk Support Administrator (LAB)
Mastering the use of Zendesk for managing tickets and enterprise support.<br />

<!--
<h2>Video Demonstration</h2>

(In progress)
- ### [YouTube: Zendesk Support Administrator]()
-->

## Environments and Technologies Used 

- Zendesk
- Windows or Mac

## Operating Systems Used

- Windows 11</b> (24H2)

## List of Prerequisites 

- Zendesk Free trial

<br>

## Desired setup
<br>
<p align="center">
<img src="https://imgur.com/K0Tt867.png"/>
</p>

The scalability of your setup highly depends on the early planning phase. Before we can go through the process of such an evaluation, we need to establish a far-reaching scenario by creating a fictitious example company. For the sake of simplicity and not having to refer to the company as an example throughout this lab, we will call it itsolutions.

itsolutions is a Canadian tech company selling their own software online. They also offer some hardware created by a third-party in order to guarantee better compatibility and support.

Next to offering their software for individual purchase, customers can choose a yearly subscription allowing them access to the full range of software solutions. These customers are called "VIPs" and can purchase the hardware to a discounted price. As part of the subscription, VIP customers are supposed to receive faster responses from the support team.

itsolutions is still considered a start-up and cannot afford to provide customer-service in more than two languages (English and French), but are planning to offer support in more languages later on.

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

- Channels
- Custom fields
- Views
- Business rules
- Agent roles
- SLAs
- Macros
- Global Zendesk settings / Security settings
- Reporting
- Zendesk apps

## So lets get started! :)
</p>


# Creating Agent Roles, Groups, Organizations, and User Tags

- Zendesk was built to communicate with millions of customers, so it is absolutely crucial to understand how we can manage our user accounts and their tickets without losing track of our processes. However, even when working with a smaller customer base, keeping scalability in mind is always a good tactic.
  
- We will go over the following:

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

- We can easily access the whole list of users by following these two steps:

1. Click on the Admin icon (gear symbol) located in Zendesk's sidebar.
2. then click "Go to Admin Center".
<br>
<p align="center">
<img src="https://imgur.com/jI9lfgN.png"/>
</p>

3. Click on "People" located in Zendesk's sidebar within the admin menu:

The types of roles available:
- Agent/Staff: Has the permissions in order to solve tickets.
- Team leader: Allows more access to the Zendesk environment.
- Advisor: Cannot solve any tickets. This role is supposed to enable the user to manage Zendesk's workflows. This entails the ability to create and edit automations, triggers, macros, views, and SLAs.
- Administrator: Has additional permissions, allowing the user to customize and manage the Zendesk environment.


## Creating Custom Agent role
We don't have the enterprise Editions, but Lets me tell you how its done.

1. Click on the Admin icon (gear symbol) located in Zendesk's sidebar.
2. Click on People located in the side menu of the admin menu.
3. Click on role.

The process of creating a custom role consists of naming and describing the role followed by defining the permissions.

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
<img src="https://imgur.com/Ye600kD.png"/>
</p>

Only allowing the necessary permission for each role.For example, Tier 1 Techs, don't need permission to view or edit reports, as well as team leads don't need access to edit dynmic contents. Best to go with least privilege in order for that role to do their specific job and nothing more.

Custom roles for our example if you have the enterprise:
- Tier 1
- Tier 2
- VIP
- Administrator


## Creating Groups
Groups are only meant for agents and each agent must be at least in one group.

In our case, we have four types of support tickets:

- Tier 1 Support
- Tier 2 Support
- VIP Support
- Internal Support

Each type of ticket is supposed to be answered by specific agents only. In order to achieve this, we will create one group for each type of ticket and later assign these groups to our agents accordingly.

In order to review and edit already existing groups, simply follow these steps:

1. Click on the Admin icon (gear symbol) located in Zendesk's sidebar.
2. Click on People located in Zendesk's sidebar within the admin menu.
3. Click on groups within the Zendesk's sidebar menu:
4. Then click the defualt group called "Support"

<br>
<p align="center">
<img src="https://imgur.com/VkVTAdY.png"/>
</p>

As per our example, we will need four groups. In order to add a new group, simply follow these steps:

1. While in the groups dashboard.
2. Click on "Add group" located at the top right of the main area.

<br>
<p align="center">
<img src="https://imgur.com/b0FBqry.png"/>
</p>

Creating a group is easy. We simply choose a name, add a description and tick the box next to each agent that we would like to be associated with this group.

Note:
There are two ways to add an agent to a group. While you may choose to navigate to the group itself in order to edit it, you can also assign groups to agents within their own user panel.

<br>
<p align="center">
<img src="https://imgur.com/7nPmiyI.png"/>
</p>


# Creating User tags
Reference Zendesk API Documentation: <a href="https://developer.zendesk.com/api-reference/ticketing/users/users/">Documentation</a>

If you have coding experience, here are the necessary code snippets:

For creating a new end-user :
```
curl -v -u {email_address}:{password} https://{subdomain}.zendesk.com/api/v2/users.json \  
-H "Content-Type: application/json"  
-X POST  
-d '{"user": {"name": "FirstName LastName", "email": "user@example.org"}}' 
```
For updating an existing user:
```
curl -v -u {email_address}:{password} https://{subdomain}.zendesk.com/api/v2/users/{id}.json \ 
-H "Content-Type: application/json"  
-X PUT  
-d '{"user": {"name": "Roger Wilco II"}}' 
```

# Importing existing user databases
In many cases, companies already have a huge amount of customers before the decision to use Zendesk has been made. In such a situation, it might be handy to have the option to import those users in bulk, especially if you like to set a user tag such as our vip tag.

Zendesk offers us two different options when it comes to importing users in bulk:

1. CSV file
2. Zendesk API

We will focus on option one as we have already covered the option to add Zendesk users, utilizing the Zendesk API when discussing user tags.

- Click on the Admin icon (gear symbol) located in Zendesk's sidebar.
- Click on People located within the admin menu.
- Click on "Import users" located on the left side of the main area under Bulk actions.
- Click on Bulk user import located on the right side of the main area (located in a grey box):

<br>
<p align="center">
<img src="https://imgur.com/3ypkASj.png"/>
</p>

Before uploading our CSV file, we can choose one or both of the following options:

1. Create new users
2. Update existing users

<br>
<p align="center">
<img src="https://imgur.com/pXRTDgU.png"/>
</p>

As we are importing new users only, we can uncheck Update existing users.


In order for the bulk-import to work, we will need to prepare our CSV file accordingly. Zendesk states the following:

- "The data must be in the comma separated values (CSV) format and saved as UTF-8."

A good way to prepare such a file is using a spreadsheet program such as Microsoft Excel. Having our example in mind, we will create an example, importing the following details:

1. Name
2. Email
3. Tags

<br>
<p align="center">
<img src="https://imgur.com/bihqNp0.png"/>
</p>

While we are only using three fields, you can find a full list of available fields and the accepted order at the following link:

<a href="https://support.zendesk.com/hc/en-us/articles/203661996-Bulk-importing-users-and-organizations">https://support.zendesk.com/hc/en-us/articles/203661996-Bulk-importing-users-and-organizations</a>

Now simply click on Choose File, locate the file on your hard drive, and confirm by clicking on Import.

Congratulations, we have successfully imported a user into our Zendesk environment!



# Creating Custom Fields

There are user fields, ticket fields, and organization fields.

- Fields are, simply put, containers for information. 
- You could say that users, tickets, and organizations are objects in Zendesk.
- Each containing a range of fields to hold the information describing the object.


## Standard ticket fields

<br>
<p align="center">
<img src="https://imgur.com/4yTCfF4.png"/>
</p>

These are the available field types before going into more detail:

- Drop-down list: Can be used in business rules.
- Text: Allows for a simple single line of text, while limiting the answer to be a short and precise string.
- Multi-line text: Allows for multiple lines of text. This can be used for instance to store a user's mailing address.
- Numeric: Allows us to limit the input to integers, reducing possible mistakes.
- Decimal: Allows us to give the option for decimal values.
- Checkbox: The answer can only be yes or no. 
- Regular expression: allows you to create a mask by entering a Ruby regular expression. This allows us to create a field limited to strings formatted in a particular way. This could be a registration key, product ID, or anything that follows strict syntax rules.
- Date: Can be used fro a user's date of birth to a deadline for a project.

To keep it simple, only the following two field types have very specific predefined options to select:

1. Drop-down list
2. Checkbox

Drop-down list
The Drop-down list allows us to predefine answers, which we can then use as a condition in business rules. We can also decide for the Drop-down list to be displayed in the support form, allowing the end-user to select one of the options. There are a few different use-case scenarios. Overall, the Drop-down list is one of the most important and useful fields in our arsenal:

## So let's go ahead and add the first custom user field:

1. Click on "User fields" located  within the admin menu.
2. Click on Checkbox located on the right within the main area.
3. Then click "Add field".

<br>
<p align="center">
<img src="https://imgur.com/OYJSszO.png"/>
</p>

We are now presented with a few options that we should take care of, before clicking on Create field:

- Display name
- Field key
- Description (optional)
- Tag (optional)

<br>
<p align="center">
<img src="https://imgur.com/zQA8qNx.png"/>
</p>

- For field title, we are going for something like "VIP". The title is self-explanatory and our agents will understand it. 
- Field key serves as an identifier for when we are using placeholders or the Zendesk API.
- Description is optional, though it cannot hurt to add additional information.
- Tag should be the same, which is vip.

Once we have filled the form to our liking, we can create the field by clicking on "Save". If you wat to create more fields, there is an option to "Save and add another".

A little checkbox with the title VIP will now show up in every user's panel. Checking the box will add the little string "vip" as a user tag. If that user decides to create a ticket, the ticket will also be tagged with "vip".


## So let's go ahead and add our first custom ticket field:

1. Click on Ticket Fields located within the admin menu on the left.
2. Click on Objects and rules.
3. Click on add field located on the top-right within the main area.


<br>
<p align="center">
<img src="https://imgur.com/uumCxSp.png"/>
</p>

4. Click Drop-down

- First, we need to find a title as it is shown to our agents within the ticket view. We can keep it simple and go with "Software".
- Next, we choose whether the drop-down can be blank when solving a ticket. In this case, we do not check the "Required to solve ticket" option as we may receive tickets that are not related to any of our third-party's software products.

5. Now it is time to add each single selectable option. Each field option consists of a Value (or Title) and a corresponding tag. You may want to follow strict rules when it comes to naming your tags with a focus on readability.

- TIP:
- Both for titles and descriptions, you are free to use dynamic content placeholders. That way, your support form can be displayed in different languages.


<br>
<p align="center">
<img src="https://imgur.com/K3ddGwV.png"/>
</p>

Once we are done adding all the software options, simply click on "Save". and we have our field showing below.

<br>
<p align="center">
<img src="https://imgur.com/T4FRGgn.png"/>
</p>


## Creating Organizational Custom Field

- And here is an Organizational Custom Field for our third party company.
- Adding custom organization fields is the same as adding user fields.

<br>
<p align="center">
<img src="https://imgur.com/2wcEbIX.png"/>
</p>


Summary:
- We learned about fields in Zendesk. 
- We learned about the general purpose of fields and how we can create and utilize the custom user, ticket, and organization fields.



# Setting Up Multiple Ticket Channels

<br>
<p align="center">
<img src="https://imgur.com/2wcEbIX.png"/>
</p>

















