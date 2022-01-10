---
title: compareVersion
tags: function,intermediate
firstSeen: 2022-01-10T02:56:11.049Z
lastUpdated: 2022-01-10T02:56:11.049Z
---

Compare two version string and return boolean

- use array and position to compare version
- compare the number in position of version array, find which one is bigger
- if the first number is equal to second number, move the position to compare next
- if one version has no next and the other one has, which one has next is bigger

```js
const compareVersion = (v1, v2) => {
  if (v1 && v2) {
    const v1Arr = v1.split(".");
    const v2Arr = v2.split(".");
    const minLength = Math.min(v1Arr.length, v2Arr.length);
    let position = 0;
    let diff = 0;
    while (
      position < minLength &&
      (diff = parseInt(v1Arr[position]) - parseInt(v2Arr[position])) === 0
    ) {
      position += 1;
    }
    diff = diff !== 0 ? diff : v1Arr.length - v2Arr.length;
    return diff > 0;
  } else {
    console.log("version lost");
    return false;
  }
};
```

```js
compareVersion("1.2.3", "1,3,1");
```
