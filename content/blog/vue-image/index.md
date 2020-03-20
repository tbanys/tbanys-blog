---
title: Working with images in vue
date: "2020-01-12T22:40:32.169Z"
description: Working with images in vue
---

# Image element in html

```javascript
<template>
  <img src="/asstes/img/img.jpg" alt="This image description">
</template>
```

# Dynamic image in vue js

Vue has special attribute for image src which is :image (short for v-bind:image), so you can provide image src dynamically

```javascript
<template>
  <img :src="image" alt="This image description">
</template>

<script>
  export default() {
    name: 'MyImage',
    data() {
      return {
        image: '/asstes/img/img.jpg'
      }
    }
  }
</script>
```

# Pass image via prop

```javascript
// Child component
<template>
  <img :src="image" alt="This image description">
</template>

<script>
  export default() {
    name: 'MyImage',
    props: ['image']
  }
</script>
```

```javascript
// Parent component
<template>
  <my-image :image="'/asstes/img/img.jpg'" />
</template>

<script>
import MyImage form './MyImage'

export default() {
  name: 'ImageWrapper',
  components: {
    MyImage
  }
}
</script>
```

# Fallback image using props

```javascript
// Child component
<template>
  <img :src="image" alt="This image description">
</template>

<script>
  export default() {
    name: 'MyImage',
    props: {
      type: String,
      default: '/asstes/img/img.jpg'
    }
  }
</script>
```

# Fallback image if src is wrong

TODO: šitam sukurti pavyzdį.

```javascript
// Child component
<template>
  <img :src="image"  alt="This image description">
</template>

<script>
  export default() {
    name: 'MyImage',
    props: {
      type: String,
      default: '/asstes/img/img.jpg'
    }
  }
</script>
```