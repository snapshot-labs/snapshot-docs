---
description: Receive event notifications with webhooks
---

# Webhooks

Snapshot uses webhooks to notify your application when an event happens. Webhooks are particularly useful for asynchronous events like when a proposal is created, when it start or when it end.

The webhook server send requests for any new event, the request are sent to custom url with `POST` method and the event object as body.

**Here is an example of event object:**

```javascript
{
  id: 'proposal/QmZ21uS8tVucpaNq2LZCbZUmHhYYXunC1ZS2gPDNWwPWD9',
  event: 'proposal/created',
  space: 'yam.eth',
  expire: 1620947058
}
```

**Here are the possible events:**

`proposal/created`  
When a new proposal is created

`proposal/start`  
When the voting period for a proposal start.

`proposal/end`  
When the voting period for a proposal end.

`proposal/deleted`  
When a proposal is deleted by the author or an admin of the space.

## Subscribe to events

If you want to subscribe to webhooks please contact us on Discord or Telegram. You will need to provide an URL to receive the webhooks requests.

