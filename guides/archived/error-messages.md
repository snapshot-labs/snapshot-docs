---
description: Information about specific errors that can appear.
---

# Error messages

| **Error code** | **Error information** |
| :--- | :--- |
| **`wrong message body`** | Message did not pass because body was empty or did not contain address or did not contain sig. |
| **`wrong signed message`** | Message did dont have his local clock sync.  |
| **`wrong timestamp`** | User doesn't have local clock synced. |
| **`wrong version`** | Hub version doesn't exist or is wrong. |
| **`wrong message type`** | Message does not include a type. |
| **`wrong signature`** | Body sig doesn't exist or is wrong. |
| **`wrong proposal format`** | Proposal must include a title, a description, 2 choices, a block time, start and end dates.  |
| **`wrong proposal size`** | Proposal size is bigger or smaller than how it should minimum/maximum be. |
| **`wrong proposal metadata`** | Proposal metadata is wrong. |
| **`wrong proposal period`** | Proposal start date is greater than the end date. |
| **`wrong vote format`** | Vote is wrong, must vote on a proposal that contains metadata and you must includea choice. |
| **`wrong vote metadata`** | Vote metadata doesn't exist or is wrong. |
| **`unknown proposal`** | Proposal is not found. |
| **`not in voting window`** | You can't vote, time didn't start yet. |

