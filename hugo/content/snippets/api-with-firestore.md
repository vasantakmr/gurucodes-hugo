---
title: API with Firestore
lastmod: 2020-03-19T14:19:51-07:00
publishdate: 2020-03-19T14:19:51-07:00
author: Vasanta Kumar
draft: true
description: Firestore bla bla bla
tags: 
    - vue
    - firebase
    - firestore
    - auth

# youtube: 
# code: 
# disable_toc: true
# disable_qna: true

# courses
# step: 0

# versions: 
#     - "rxjs": 6.3
---



Firebase is an excellent stack for building realtime apps at any scale.


## Initial Setup

getting started with Firebase.

{{< file "js" "firebase.js" >}}
```javascript
import firebase from 'firebase/app';
import 'firebase/firestore';
import 'firebase/auth';

const firebaseConfig = { 
  // your config here
};

firebase.initializeApp(firebaseConfig);

export const app = firebase.app();
export const db = firebase.firestore();
```


## User Component

It can be very useful.

{{< file "js" "User.js" >}}
```html
<template> 
    <div>
        <p></p>
    </div>
</template>
```