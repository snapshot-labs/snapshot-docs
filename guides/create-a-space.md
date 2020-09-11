# Create a space

### **1: Fork Snapshot spaces repository here**

{% embed url="https://github.com/bonustrack/snapshot-spaces" %}

### **2: Copy the space example folder**

{% embed url="https://github.com/bonustrack/snapshot-spaces/tree/master/spaces/example" %}

```yml
|-- spaces
    |-- example
        |-- index.json
        |-- logo.png
        |-- skin.scss
        |-- space.png
```

### **3: Change your space metadata**

* The name of the folder must be the key of your space.
* This key also corresponds to the slug url and must not be composed with uppercase characters. `"key": "example"` to `"key": "my-space"`

`index.json`
```json
{
  "key": "example",
  "symbol": "EXAMPLE",
  "name": "Example",
  "defaultView": "core",
  "address": "0xC02aaA39b223FE8D0A0e5C4F27eAD9083C756Cc2",
  "token": "0xC02aaA39b223FE8D0A0e5C4F27eAD9083C756Cc2",
  "core": [
    "0xeF8305E140ac520225DAf050e2f71d5fBcC543e7"
  ],
  "min": 0,
  "invalid": []
}
```

### **4: Add a logo and space images** 
* You must add both `logo.png` and `space.png` images for your space with a size of 256 x 256 pixels.

### **5: Create a skin \(optional\)**

* If you want the default skin you can delete the file `skin.scss`.
* If you want a skin you can change colors in the file `skin.scss` and change the `.name` to the id of your space. `.name` to `.my-space`

`skin.scss`
```scss
.name {
  --primary-color: #384aff;
  --bg-color: white;
  --text-color: #586069;
  --link-color: #111111;
  --heading-color: #111111;
  --border-color: #d1d5da;
  --header-bg: white;
  --block-bg: transparent;
}
```

### **6: Make a pull request**

It may take 1 or 2 days to get your PR reviewed , merged and appear on Snapshot. 

