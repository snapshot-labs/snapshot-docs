# Migrate your space to ENS

### 1. Create a space with ENS

To migrate your space you will need first to create the space with ENS.   
  
You can use this url to get your previous space settings populated in the form: https://snapshot.page/\#/**&lt;ens\_space\_id&gt;**/settings/**&lt;previous\_space\_id&gt;**  
Example: https://snapshot.page/\#/**yam.eth**/settings/**yam**

{% page-ref page="create-a-space.md" %}

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

### 3. Migrate proposals, votes and urls

The migration of the proposals, votes and urls is done manually, once your space with ENS is ready please contact an admin on [Discord](https://discord.snapshot.page) to do the changes.

