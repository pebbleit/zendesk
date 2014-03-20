# Foration notifications

A list of [triggered](https://support.zendesk.com/entries/20011606) email notifications Foration might receive from **[pebble.it help!](http://help.pebbleit.com)**. See the [Zendesk data object (placeholders) reference](https://support.zendesk.com/entries/20203943) and [Liquid](https://github.com/Shopify/liquid/wiki/Liquid-for-Designers) for help with the markup.

## Primer

The Foration Zendesk `Agent` has the email address [pebble@foration.com](mailto:pebbleit@foration.com) – all Zendesk notifications are sent to this address.

Zendesk notifications are sent in the form (example headers snippet):

	From: "pebble.it Help!" <help@pebbleit.com>
	To: "Foration Support" <pebbleit@foration.com>
	Reply-To: "pebble.it Help!" <help@pebbleit.com>
	Message-ID: <99H29TP8_531eaee178f82_3e583fd20fec9ea81422d6_sprut@zendesk.com>
	In-Reply-To: <99H29TP8@zendesk.com>
	Subject: [pebble.it help!] Re: Ticket Subject

To update a ticket, Foration send email updates in the form (corresponding example headers snippet):

	From: pebbleit@foration.com
	To:  help@pebbleit.com
	In-Reply-To: <99H29TP8_531eaaa8ac0c0_43b33fa7db4c9eac407071_sprut@zendesk.com>
	References: <99H29TP8@zendesk.com>  
	<99H29TP8_531eaaa8ac0c0_43b33fa7db4c9eac407071_sprut@zendesk.com>


Please note, update emails:

1. **Must** be sent from pebbleit@foration.com (otherwise will create new ticket or produce ‘unknown user’ bounce)
2. **Must** be sent to help@pebbleit.com
3. **Must** include the headers References and/or In-Reply-To (with data corresponding to the ticket)

The message body can contain ticket property updates and/or comments, as described by the [Zendesk Mail API](https://support.zendesk.com/entries/21543427).

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
	#Organisation: {{ticket.organization.name}}
	#Priority: {{ticket.priority}}
	#Type: {{ticket.ticket_type}}
	#Origin: Email
	
	Ticket history follows.
	
	*** Comment Start ***
	{{ticket.comments_formatted}}
	*** Comment End ***

## Ticket update

### Notify Foration of comment update

Informs Foration of a new comment (public or private) added to ticket to which they are assigned. Will not trigger for Foration’s own updates, or for ‘reopens’ (separate notification, below).

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

Informs Foration their ticket has been reopened (any `Status` change from `Solved`, other than `Closed`). Will not trigger if the Foration reopen their own ticket.

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
	{{ticket.comments_formatted}}
	*** Comment End ***
