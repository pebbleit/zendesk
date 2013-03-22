# End-user notifications

A list of automated email notifications the `Requester` receives from **[pebble.it help!](http://help.pebbleit.com)**. See the [Zendesk data object (placeholders) reference](https://support.zendesk.com/entries/20203943) and [Liquid](https://github.com/Shopify/liquid/wiki/Liquid-for-Designers) for help with the markup.

## Pending requests

### Pending notification 24 hours

Sent to the `Requester` if a ticket is `Pending` for 24 hours.

Email subject:

	[{{ticket.account}}] Pending request: {{ticket.title}}

Email body:

	This is an email to remind you that your request (#{{ticket.id}}) is pending and awaits your feedback.
	
	{{ticket.comments_formatted}}

### Pending notification 5 days

Sent to the `Requester` if a ticket is `Pending` for 120 days.

Email subject:

	[{{ticket.account}}] Pending request: {{ticket.title}}

Email body:

	This is an email to remind you that your request (#{{ticket.id}}) is pending for 5 days and awaits your feedback.
	
	{{ticket.comments_formatted}}

## Customer satisfaction

### Request customer satisfaction rating

Sent to the `Requester` 24 hours after a ticket is `Solved`. Not offered to _Foration Support_, _Siplu Mitu_, and _Dave Rosen_ assigned tickets

Email subject:

	[{{ticket.account}}] Request #{{ticket.id}}: How would you rate the support you received?

Email body:

	Hello {{ticket.requester.first_name}},
	
	We'd love to hear what you think of our customer service. Please take a moment to answer one simple question by clicking either link below:
	
	{{satisfaction.rating_section}}
	
	Here's a reminder of what your ticket was about:
	
	{{ticket.comments_formatted}}
	
	Regards,
	pebble.it help!
