# Agent notifications

A list of automated email notifications an `Agent` receives from **[pebble.it help!](http://help.pebbleit.com)**. See the [Zendesk data object (placeholders) reference](https://support.zendesk.com/entries/20203943) and [Liquid](https://github.com/Shopify/liquid/wiki/Liquid-for-Designers) for help with the markup.

## Unassigned requests

### Unassigned notification 1 hour

Sent to all `Agents` in the `Group` of an unassigned ticket after 1 business hour.

Email subject:

	[Zendesk] Unassigned: {{ticket.title}}

Email body:

	This ticket (#{{ticket.id}}) by {{ticket.requester.name}} remains unassigned.
	
	Review it by following the link below:
	{{ticket.url_with_protocol}}
	
	{{ticket.comments_formatted}}
