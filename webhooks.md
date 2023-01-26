---
description: Receive event notifications with webhooks.
---

# Webhooks

Snapshot uses webhooks to notify your application when an event happens. Webhooks are particularly useful for asynchronous events like when a proposal is created, when it starts, or when it ends.

The webhook server sends a request for any new event, the request is sent to the configured URL with `POST` method and the event object as body.&#x20;

**Here is an example of the event object:**

```javascript
{
  id: 'proposal/QmZ21uS8tVucpaNq2LZCbZUmHhYYXunC1ZS2gPDNWwPWD9',
  event: 'proposal/created',
  space: 'yam.eth',
  expire: 1620947058
}
```

**Here are the possible events:**

`proposal/created` \
When a new proposal is created

`proposal/start` \
When the voting period for a proposal starts.

`proposal/end` \
When the voting period for a proposal ends.

`proposal/deleted`  \
When a proposal is deleted by the author or an admin of the space.

### Subscribe to events

If you want to subscribe to webhooks please contact us on [Discord](https://discord.snapshot.org) in this [#helpdesk thread](https://discord.com/channels/707079246388133940/1061160799407702029/1061160799407702029). You will need to provide an **URL** to receive the webhook request.

### Test a webhook

You can use this URL [https://webhook.snapshot.org/api/test?url=https://example.com](https://webhook.snapshot.org/api/test?url=https://example.com) and change example.com with your own endpoint to trigger a test callback.
