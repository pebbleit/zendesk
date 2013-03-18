# Foration notifications

A list of email nofitications Foration might receive from **[pebble.it help!](http://help.pebbleit.com)**. See the [Zendesk data object (placeholders) reference](https://support.zendesk.com/entries/20203943) and [Liquid](https://github.com/Shopify/liquid/wiki/Liquid-for-Designers) for help with the markup.

The Foration Zendesk `Agent` has the email address pebble@foration.com – all Zendesk notifications are sent to this address.

## Ticket assignment

### Notify Foration of assignment

Triggers when a pebble.it Zendesk `Agent` assigns a ticket to Foration. Will not be triggered if Foration ‘take’ a ticket via the Zendesk web interface (self-assignment).

Email subject:

	pebble.it ticket assignment: #{{ticket.id}}

Email body:

	{{ticket.assignee}} has been assigned a ticket in pebble.it Zendesk.
	
	Ticket details follow.
	
	#TicketId: {{ticket.id}}
	#Subject: {{ticket.title}}
	#Created: {{ticket.created_at}}
	#Status: {{ticket.status}}
	#Firstname: {{ticket.requester.first_name}}
	#Lastname: {{ticket.requester.last_name}}
	#Email: {{ticket.requester.email}}
	#Organisation: {{ticket.organization.name}}#Priority: {{ticket.priority}}
	#Type: {{ticket.ticket_type}}
	#Origin: Email
	
	Ticket history follows.
	
	*** Comment Start ***
	{{ticket.comments_formatted}}
	*** Comment End ***

## Ticket update

### Notify Foration of comment update

Informs Foration of a new comment (public or private) added to ticket to which they are assigned. Will not trigger for Foration’s own updates, or for ‘reopens’ (seperate notification, below).

Email subject:

	pebble.it ticket updated: #{{ticket.id}}

Email subject:

	{{updater.name}} has updated a ticket in pebble.it Zendesk.
	
	Ticket details follow.
	
	#TicketId: {{ticket.id}}
	#Subject: {{ticket.title}}
	#Created: {{ticket.created_at}}
	#Status: {{ticket.status}}
	#Firstname: {{ticket.requester.first_name}}
	#Lastname: {{ticket.requester.last_name}}
	#Email: {{ticket.requester.email}}
	#Organisation: {{ticket.organization.name}}
	#Priority: {{ticket.priority}}
	#Type: {{ticket.ticket_type}}
	#Origin: Email
	
	*** Comment Start ***
	{{ticket.latest_comment_formatted}}
	*** Comment End ***

## Ticket reopened

### Notify Foration of reopened ticket

Informs Foration their ticket has been reopened (any `Status` change from `Solved`, other that `Closed`). Will not trigger if the Foration reopen their own ticket.

Email subject:

	pebble.it ticket reopened: #{{ticket.id}}

Email body:

	{{updater.name}} has reopened a ticket in pebble.it Zendesk.
	
	Ticket details follow.
	
	#TicketId: {{ticket.id}}
	#Subject: {{ticket.title}}
	#Created: {{ticket.created_at}}
	#Status: {{ticket.status}}
	#Firstname: {{ticket.requester.first_name}}
	#Lastname: {{ticket.requester.last_name}}
	#Email: {{ticket.requester.email}}
	#Organisation: {{ticket.organization.name}}
	#Priority: {{ticket.priority}}
	#Type: {{ticket.ticket_type}}
	#Origin: Email
	
	*** Comment Start ***
	{{ticket.latest_comment_formatted}}
	*** Comment End ***