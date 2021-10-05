# Migrate your space to ENS

If you already have a space in Snapshot which does not have an ENS name, you need to migrate your space to ENS. The following guide takes through the procedures of how to successfully migrate your space to ENS.

### 1. Create a space with ENS

To migrate your space you will need first to create the space with ENS.   
  
You can use this url to get your previous space settings populated in the form: https://snapshot.page/\#/**&lt;ens\_space\_id&gt;**/settings/**&lt;previous\_space\_id&gt;**  
Example: https://snapshot.page/\#/**yam.eth**/settings/**yam**

{% page-ref page="create.md" %}

### 2. Declare your new space alias

To add your new space alias you need to do a pull request on this repository:

{% embed url="https://github.com/snapshot-labs/snapshot-spaces" %}

#### Follow the Snapshot spaces directory tree

```bash
└── spaces
    └── aliases.json
```

You must add your new alias in the [aliases.json file](https://github.com/snapshot-labs/snapshot-spaces/blob/master/spaces/aliases.json) by following this example.

```javascript
{
  "my-space": "my-space.eth"
}
```

### 3. Migrate proposals, votes and URLs

The migration of the proposals, votes, and URLs is done manually, once your space with ENS is ready please send us a message on the "helpdesk" channel on [Discord](https://discord.snapshot.page) to do the changes.

You have now successfully migrated your space to ENS! The next guide will take you through steps for adding an avatar and skin for your space.

