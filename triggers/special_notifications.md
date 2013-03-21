# Special notifications

A list of [triggered](https://support.zendesk.com/entries/20011606) custom email nofitications sent from **[pebble.it help!](http://help.pebbleit.com)**. See the [Zendesk data object (placeholders) reference](https://support.zendesk.com/entries/20203943) and [Liquid](https://github.com/Shopify/liquid/wiki/Liquid-for-Designers) for help with the markup.

## Requester

### Notify requester of correct address

Designed to inform the `Requester` their original request was sent to the wrong address and point them in the right direction for next time. Triggered when a ticket is created, containing any of the following strings:

* [support]
* support@pebbleit.com
* info@pebbleit.com
* help@pebbleit.com
* tag@pebbleit.com

Email subject:

	[{{ticket.account}}] Please update your contacts

Email body:

	Hello {{ticket.requester.first_name}},
	
	We detected you may have used an incorrect address to generate this request.
	
	Next time, please email help@pebbleit.com. This will ensure the fastest response.
	
	Regards,
	pebble.it help!

## Assignee

### Enter :: everyone@ reminder

Designed to remind the `Agent` that any _Enter_ new mail account should be included in their _everyone_ mailing list. Triggered when an Enter ticket is `Solved` with the _newuser_ plus either _kerio_ or _kerioconnect_ tags.

Email subject:

	[Zendesk] reminder

Email body:

	It looks like you just made a new email account(s) for {{ticket.requester.first_name}}. Did you remember to add them to the everyone@ mailing list?
	
	Fond regards,
	Big Brother

## Other

### Notify James of Foration update

Informs _James_ that _Foration_ have updated a ticket.

Email subject:

	[Zendesk] Foration updated: {{ticket.title}}

Email body:

	This ticket (#{{ticket.id}}) has been updated by {{current_user.name}}.
	
	{{ticket.latest_comment_formatted}}

### Loaf :: Notify Jess of received request

To inform _Jess_ of any new _Loaf_ requests. _Jess_ has permission to see all tickets in her `Organisation`, so one informed she can track progress in the Zendesk web interface.

Email subject:

	[{{ticket.account}}] "{{ticket.title}}" from {{ticket.requester.name}}

Email subject:

	A ticket (#{{ticket.id}}) by {{ticket.requester.name}} has been received.
	
	Review it by following the link below:
	http://{{ticket.url}}
	
	{{ticket.comments_formatted}}

### Negative feedback notification

Informs _David_ when a negative satisfaction rating is received.

Email subject:

	[Zendesk] Negative feedback: {{ticket.title}}

Email body:

	Oh noes! {{ticket.requester.name}} ({{ticket.organization.name}}) gave a bad feedback rating on this ticket (#{{ticket.title}}). Their satisfaction comment (if any) was:
	
	"{{satisfaction.current_comment}}"
	
	Assignee: {{ticket.assignee.name}}
	
	To review the ticket, follow the link below:
	{{ticket.url_with_protocol}}