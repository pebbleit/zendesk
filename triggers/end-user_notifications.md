# Standard End-User notifications

A list of [triggered](https://support.zendesk.com/entries/20011606) email nofitications a client/customer (the `Requester`) receives from **[pebble.it help!](http://help.pebbleit.com)**. See the [Zendesk data object (placeholders) reference](https://support.zendesk.com/entries/20203943) and [Liquid](https://github.com/Shopify/liquid/wiki/Liquid-for-Designers) for help with the markup.

## Ticket received

### Notify requester of received request

Informs `Requester` a ticket has been created in Zendesk. Any method (email, web…), any user (`Requester` themselves or by `Agent`)

Email subject:

	[{{ticket.account}}] Request received: {{ticket.title}}

Email body:

	Your request (#{{ticket.id}}) has been received and is being reviewed by our support staff.
	
	To add additional comments, reply to this email or click the link below:
	{{ticket.url_with_protocol}}
	
	{{ticket.comments_formatted}}

## Ticket update

### Notify requester of comment update

Informs `Requester` of a new ‘visible’ (public in most cases) comment added to their ticket. Will not trigger for the `Requester`’s own updates, or if `Status` is changed to `Solved` (seperate trigger, below).

Email subject:

	[{{ticket.account}}] Re: {{ticket.title}}

Email subject:

	Your request (#{{ticket.id}}) has been updated. Reply to this email or click the link below:
	{{ticket.url_with_protocol}}
	
	{{ticket.comments_formatted}}

## Ticket solved

### Notify requester of solved request

Informs `Requester` their ticket has been solved. Only triggers if a visible comment is also present.

Email subject:

	[{{ticket.account}}] Re: {{ticket.title}}

Email body:

	Your request (#{{ticket.id}}) has been deemed solved. To reopen this request, reply to this email or click the link below:
	{{ticket.url_with_protocol}}
	
	{{ticket.comments_formatted}}
