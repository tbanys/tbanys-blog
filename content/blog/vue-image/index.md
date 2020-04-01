---
title: Working with images in vue
date: "2020-01-12T22:40:32.169Z"
description: Display images in Vue
---

# Displaying image in vue js

First of all if you want to display image on internet you have to know it's url or src. I won't cover it here, because there is multiple ways to know that.
Let's asume you already know you image source and you want to display image in Vue.

There is multiple cases when you have to display image I will try to cover most freaquent ones.


First and the most sipliest way to display image is just the same as you do in your html when you displaying static images.
If you want to display image which is static you can do it simply like that:

Static image

# Image element in html

```javascript
<template>
  <img src="/asstes/img/imageFile.jpg" alt="Image description">
</template>
```


# Dynamic image in vue js

If url is dynamic, then you need to use directive v-bind and bind src attribute like that v-bind:src or shorthand :src.


Vue template will look like that

```javascript
<template>
  <img :src="imageFile" alt="Image description">
</template>
```

Get image from data
```javascript
<script>
  export default() {
    name: 'MyImage',
    data() {
      return {
        imageFile: '/asstes/img/imageFile.jpg'
      }
    },
  }
</script>
```

Get image from computed

```javascript
<script>
  export default() {
    name: 'MyImage',
    computed: {
      imageFile() {
        return '/asstes/img/imageFile.jpg';
      }
    }
  }
</script>
```

Get image from methods

```javascript
<script>
  export default() {
    name: 'MyImage',
    methods: {
      imageFile() {
        return '/asstes/img/imageFile.jpg';
      }
    }
  }
</script>
```

Also with v-bind src you can use with inline string concatenation:

```javascript
<template>
  <img :src="'/asstes/img/imageFile'" alt="This image description">
</template>
```

```javascript
<template>
  <img :src="'/asstes/img/' + imageFile" alt="This image description">
</template>

<script>
  export default() {
    name: 'MyImage',
    data() {
      return {
        image: 'img.jpg'
      }
    }
  }
</script>
```

# Pass image via prop

You can provide image src with prop from parent component:

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

# Fallback image using props

Sometimes, when you work with big project not always image is provided, then you need to set default image if for some reason image is not provided.
You can simply do it like with prop and set default value. Then if parent component provide empty image then you can always show default one:

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

# Fallback image if src has broken link

What to do if you have broken image link? Display placeholder instead.

But also, sometimes api provides broken image url, then default image won't work here. You have to add @onerror hook or something like that.

In this case we can use default image, because image property is provided and not empty, we have to use method which will change image src on error.

```javascript
// Child component
<template>
  <img :src="image" @error="displayPlaceholder"  alt="This image description">
</template>

<script>
  export default() {
    name: 'MyImage',
    props: {
      type: String,
      default: '/asstes/img/brekonImg.jpg'
    },
    data: {

    },
    methods: {
      displayPlaceholder(event) {
        event.target.src = "placeholder.jpg"
      }
    }
  }
</script>
```

This is different ways to display image in you vue js application.