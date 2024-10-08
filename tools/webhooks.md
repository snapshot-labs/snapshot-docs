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

### Test a webhook

You can use this URL [https://webhook.snapshot.org/api/test?url=https://example.com](https://webhook.snapshot.org/api/test?url=https://example.com) and change example.com with your own endpoint to trigger a test callback.

### Subscribe to events

If you want to subscribe to Webhooks, please fill out this [form](https://tally.so/r/mVQZQl), \
\
If you don't receive events even after 48 hours after filling the form, please contact our support on [Help Center](https://help.snapshot.org/en/)
