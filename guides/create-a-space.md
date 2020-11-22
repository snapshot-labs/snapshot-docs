# Create a space with ENS \(beta\)

### 1. Get an ENS domain for your space

If you don't have an ENS domain yet for your space you can register one here: [https://app.ens.domains](https://app.ens.domains/)

### 2. Link your ENS domain to Snapshot with "contenthash"

* Go on this url: https://snapshot.page/\#/my-space.eth/settings \(change `my-space.eth` with your ENS domain\).
* Copy the IPNS link in the ENS field.
* Click on the button "Set record on ENS", you will get redirected to ENS app.
* On the ENS app click on "ADD/EDIT RECORD".

![](../.gitbook/assets/image%20%283%29.png)

* Paste the IPNS link in the "CONTENT" field.
* Click confirm and submit the change.

![](../.gitbook/assets/image%20%285%29.png)

### **3. Setup your space settings**

* Refresh the page https://snapshot.page/\#/my-space.eth/settings.
* Now you can edit your space settings
* Click "Save" and sign settings message on your wallet.
* Now you are set! You can go on https://snapshot.page/\#/my-space.eth to see your space.

{% hint style="info" %}
When you create or edit a space, it take about 2min to see the changes live.
{% endhint %}

### **4. Add your space logo and strategy image\(s\)**

To get a logo for your space and images for the strategies you need to do a pull request on this repository [https://github.com/snapshot-labs/snapshot-spaces](https://github.com/snapshot-labs/snapshot-spaces). You will need to create a folder with the id of your space \(example: "my-space.eth"\). In this folder you need a file "space.png" and "logo.png" \(for the first strategy\) and "logo1.png" if you have a second strategy. All the images must be squared and less than 50kb. 

