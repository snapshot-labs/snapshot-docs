---
description: Learn how to create a new plugin for Snapshot.
---

# Create a plugin

If the existing plugins do not fulfill the needs of your space it is possible to create a new one. Keep in mind though that at this moment we have a curated list of plugins that extend the core funcitonality of Snapshot and we want to make sure that their logic is written in line with Snapshot's values.

{% hint style="info" %}
The development of new plugins should be coordinated with the Snapshot team.&#x20;
{% endhint %}

## 1. Fork the snapshot repository

Create a fork of the **snapshot** repository:

{% @github-files/github-code-block url="https://github.com/snapshot-labs/snapshot/tree/" %}

## 2. Create a new directory and the plugin.json

Position yourself at the root of the project repository and run the below command to create a new directory for your plugin and provide basic details about it.

\
Make sure to update `myPlugin` with the name of your plugin (using `camelCase` naming convention), `name` and `description` to briefly describe what it does:

```shell
mkdir src/plugins/myPlugin && echo '{
  "name": "My Snapshot Plugin",
  "author: "My GH profile",
  "version": "1.0.0",
  "description": "A plugin to show how plugins are built.", # optional
  "defaults": {}, # predefined parameters, optional
  "icon": "", # URL for the icon, optional
  "website": "https://my.website" # optional
}' > src/plugins/myPlugin/plugin.json
```

Thanks to the `plugin.json` file the plugin will be visible in the space settings.

You can check that by running the local server and heading to any space's settings.

Now it's time to add the logic to it!

## 3. Create plugin structure and logic&#x20;

In order to display the plugin on Snapshot, you need to create its structure by using components. The below table is listing the available components with their render location:&#x20;

| Plugin component               | will be rendered here:          |
| ------------------------------ | ------------------------------- |
| `myPlugin/Proposal.vue`        | below proposal content          |
| `myPlugin/ProposalSidebar.vue` | proposal sidebar                |
| `myPlugin/Create.vue`          | proposal creation, plugins step |

Within those components you can do everything you can do in any other Vue 3 component. You can split the code across multiple components and import them in one of the above, as well as create your own **composables** or other **helper** files to structure your code as you like.

It's technically not required but recommended to use Vue 3's composition API and the `<script setup>` syntax.

Let's have a look at the **Proposal** component example.

### Proposal

In order to display your plugin below the proposal content you have to create a **Proposal** component. Navigate to the plugin directory you have just created in the previous step and create a `Proposal.vue` file. You can start with a basic Vue.js single file component.

```
<script setup>
const msg = 'Hello world!'
</script>

<template>
  <h1>My Plugin</h1>
  <div>{{ msg }}</div>
</template>
```

### Properties

To do something meaningful, a plugin will probably need some awareness of the current context (space, proposal, etc). **This information is passed down to the plugin components as properties**. A component on the proposal page, that needs the proposal's id can receive it in the following way:

```
<script setup>
defineProps({
  id: String // the current proposal's id
});
</script>

<template>
  <a :href="'https://...' + id"> ...
</template>
```

Here are all properties, that will be passed down to the plugin's main components:

|                   | Create form     | Proposal page                           |
| ----------------- | --------------- | --------------------------------------- |
| **proposal**      | form content    | current proposal                        |
| **space**         | space settings  | space settings                          |
| **preview**       | preview enabled | -                                       |
| **id**            | -               | proposal id route parameter             |
| **results**       | -               | current voting results                  |
| **loadedResults** | -               | whether voting results finished loading |
| **strategies**    | -               | used strategies                         |

Only the main components (`Create.vue`, `Proposal.vue`, `ProposalSidebar.vue`) in your plugin's root directory will receive those properties automatically. You can of course pass those properties further down to other components as needed.

### Existing components/composables

Any of the existing UI components in `src/components`, composables in `src/composables` or installed packages (like [snapshot.js](https://docs.snapshot.org/snapshot.js)) can be used normally.

```
<script setup>
import { useWeb3 } from '@/composables/useWeb3'
const { web3Account } = useWeb3();
</script>

<template>
  <Block title='My Plugin'>
    <h2>Your Account: {{ web3Account }}</h1>
  </Block>
</template>
```

### Config defaults

Most plugins will require some configuration options so that a space admin can enter information like their token address, API endpoints and others. Defaults can be defined in the `plugin.json` as follows:

```json
{
  "name": "My Snapshot Plugin",
  "description": "A plugin to show how plugins are built.",
  "defaults": {
    "space": {
      "someURL": "https://..."
    },
    "proposal": {
      "someParam": true
    }
  }
}
```

Under the `"space"` key you can define global config options. They can then be set in the plugin section on a space's settings like so:\


<figure><img src="../.gitbook/assets/image (75).png" alt=""><figcaption></figcaption></figure>

The `"proposal"` key let's you define options specific to a single proposal. This key must be set in order for the `Create.vue` component to be shown in the proposal creation process.

### Localization

The snapshot.org interface supports multiple languages and new plugins should be built with that in mind. Don't use raw text strings in your plugin's components directly but use the `t` function instead:

```
<template>
  <h1>{{ $t('myPlugin.hello') }}</h1>
</template>
```

The actual strings need to be added in `src/locales/default.json` to be available for translators, in order to update the language specific files, like `de-DE.json`. You can add your strings on the highest level in `default.json`, under a unique key, e.g. your plugin's directory name and the translation will be done automatically.

```json
{
  "myPlugin": {
    "hello": "Hello World!"
  }
}
```

Learn more about localization in Vue [here](https://vue-i18n.intlify.dev/).

### Numbers and relative time

Apart from `vue-i18n`, there are custom number and time formatters available in the `useIntl` composable.

```
<script setup>
import { useIntl } from '@/composables/useIntl';

const {
  formatRelativeTime,
  formatDuration,
  formatNumber,
  formatCompactNumber,
  formatPercentNumber
} = useIntl();
</script>

<template>
  <div>
    {{ formatRelativeTime(1643350286) }} <!-- "5 minutes ago" -->
    {{ formatDuration(654) }}            <!-- "11 minutes" --> 
    {{ formatNumber(1643350) }}          <!-- "1,643,350" -->
    {{ formatCompactNumber(1643350) }}   <!-- "1.6M" -->
    {{ formatPercentNumber(0.86543) }}   <!-- "86.54%" -->
  </div>
</template>
```

## 4. Create a Pull Request

Once your plugin is tested and ready to deploy, create a new Pull Request on the original[ **snapshot repository**](https://github.com/snapshot-labs/snapshot)**.**\
The review can take the team up to 72 hours, so please be patient 🙏

After the PR has been merged, you will need to wait for the release of a new version of [Snapshot](https://snapshot.org) which can take a couple of days.

## 5. Test the plugin in production

Your plugin is now available on Snapshot! :tada: Make sure to **test it thoroughly in production** before communicating to your community.
