# Agent notifications

A list of email nofitications an `Agent` might receive from **[pebble.it help!](http://help.pebbleit.com)**. See the [Zendesk data object (placeholders) reference](https://support.zendesk.com/entries/20203943) and [Liquid](https://github.com/Shopify/liquid/wiki/Liquid-for-Designers) for help with the markup.

## New tickets

### Notify Group of assignment

Most likely the first email notification an `Agent` receives for a new ticket (`Requester` or their `Organisation` should be mapped to a `Group`, usually `Support`). Each `Agent` in the `Group` recieves a copy of this notice.

Email subject:

	[Zendesk] "{{ticket.group.name}}" assignment: {{ticket.title}}

Email body:

	This ticket (#{{ticket.id}}) has been assigned to group '{{ticket.group.name}}', of which you are a member. 
	
	To review the status of the ticket, follow the link below:
	http://{{ticket.url}}
	
	{{ticket.comments_formatted}}

### Notify all Agents of received request

The first email notification an `Agent` receives for a new ticket not assigned to a `Group` (`Requester` or their `Organisation` is not mapped to a `Group`).

Sent to `Non-restricted Agents` only (currently all pebble.it Agents).

Email subject:

	[Zendesk] {{ticket.title}}

Email body:

	A ticket (#{{ticket.id}}) by {{ticket.requester.name}} has been received. Is is unassigned.
	
	Review it by following the link below:
	http://{{ticket.url}}
	
	{{ticket.comments_formatted}}

## Ticket assignment

### Notify Assignee of assignment

To inform `Agent` he is assigned a ticket. Not triggered on self-assigment.

Email subject:

	[Zendesk] Assignment: {{ticket.title}}

Email body:

	You have been assigned to this ticket (#{{ticket.id}}).
	
	To review the status of the ticket and add updates, follow the link below:
	http://{{ticket.url}}
	
	{{ticket.comments_formatted}}

## Ticket update

### Notify assignee of comment update

Informs `Agent` of a new comment (public or private) added to their ticket. Will not trigger for the `Agent`’s own updates, or for ‘reopens’ (seperate notification, below).

Email subject:

	[Zendesk] Re: {{ticket.title}}

Email subject:

	This ticket (#{{ticket.id}}) has been updated.
	
	To review the status of this ticket and add updates, follow the link below:
	http://{{ticket.url}}
	
	{{ticket.latest_comment_formatted}}

## Ticket reopened

### Notify assignee of reopened ticket

Informs `Agent` their ticket has been reopened (any `Status` change from `Solved`, other than `Closed`). Will not trigger if the `Agent` reopens their own ticket.

Email subject:

	[Zendesk] Re: {{ticket.title}}

Email body:

	This ticket (#{{ticket.id}}) has been reopened.
	
	To review the status of this ticket and add updates, follow the link below:
	http://{{ticket.url}}
	
	{{ticket.comments_formatted}}
