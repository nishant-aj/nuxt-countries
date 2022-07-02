# Basics of Vue development

## Table of Contents

- [Vue file structure](#vue-file-structure)
- [Adding some HTML and CSS content](#adding-some-html-and-css-content)
- [Adding some JS code](#adding-some-js-code)
- [Integrating HTML and JS](#integrating-html-and-js)
  - [Other important Vue Directives](#other-important-vue-directives)
    - [v-if](#v-if)
    - [v-else](#v-else)
    - [v-else-if](#v-else-if)
    - [v-for](#v-for)
    - [v-bind](#v-bind)

## Vue file structure

All files that end in `.vue` are Vue files. They consist of 3 parts (all optional based on your code). They are "The JS part", "The CSS part", and "The HTML part".

`app.vue`:

```vue
<script>
// The JS part
</script>

<template>
<!-- The HTML part -->
</template>

<style>
/* The CSS part */
</style>
```

## Adding some HTML and CSS content

Referencing to our orientation website that we created, the HTML part of the `app.vue` file should be like:

```vue
<template>
  <div>
    <h1>Heading tag</h1>
    <h2>My first website</h2>
    <button>Click me</button>
    <p>Number of clicks: 0</p>
  </div>
</template>

<style>
body {
  padding: 0;
  margin: 0;
}

h1 {
  width: 100%;
  text-align: center;
  background-color: green;
  color: white;
  margin: 0;
}

button {
  box-shadow: 0 0 8px 4px lightgrey;
}
</style>
```

Right now, if you run this code, it will not work because we didn't add any JavaScript code.

## Adding some JS code

At first, we need to have a stateful reactive object. A **reactive** variable is one that re-renders the DOM(Document-Object Modal) when its value changes. We also need to have a function that would increment the value of this variable whenever invoked. Let's try that.

```vue
<script setup>
const number = ref(0)

function handleClick() {
  number.value++
}
</script>
```

*Note*: the `setup` keyword after the script is important

`ref` is a function that is provided by Vue that tells the framework that `number` is a reactive variable; whenever there is any change in its value, re-render the entire vue file.

However, this still wouldn't work on the browser because we did not connect the two together.

## Integrating HTML and JS

Inside the `<template />`, we have our HTML content. We need to attach the button to the `handleClick` function. We can perform this by adding the following *vue directive*

```vue
<template>
    <!-- code -->
    <button v-on:click="handleClick">Click me</button>
</template>
```

`v-on:click` is the means that whenever the button is clicked, the `handleClick` function will be called; thereby, incrementing the value of number.

We also need to reflect the number in the next line (inside the `<p />`)

```vue
<template>
    <!-- v-on: can be replaced with @ -->
    <button @click="handleClick">Click me</button>
    <p>Number of clicks: {{ number }}</p>
</template>
```

To display any variable inside the `<template />`, we use the double curly brackets to do so. Run your code and you will be able to see the number incrementing on every click.

**Note**: We need to have be careful that reference variables need to use the `#value` property (`number.value++`) inside the `<script />`. But inside the HTML, we need to simply use the variable as itself(`number`)

### Other important Vue Directives

We have already taken a look at `v-on` which calls a function with every event. Let's look at other vue directives as well.

#### v-if

This Vue directive accepts a boolean expression. If the expression evaluates to `true`, then the follow content is shown; or else it is hidden. For example,

```vue
<template>
    <!-- code -->

    <div v-if="number < 10">
      Too Small
    </div>
</template>
```

At first, you shall see this div. But once `number` reaches 10, "Too small" is disappeared.

#### v-else

`v-else` must be used in conjunction with `v-if`. Naturally, it will be rendered if the original expression evaluates to `false`.

```vue
<template>
    <!-- code -->

    <div v-if="number < 10">
      Too Small
    </div>
    <div v-else>
      Too Large
    </div>
</template>
```

#### v-else-if

An amalgamation of the two previous vue directives.

```vue
<template>
    <!-- code -->

    <div v-if="number < 10">
      Too Small
    </div>
    <div v-else-if="number < 20">
      Just enough
    </div>
    <div v-else>
      Too Large
    </div>
</template>
```

#### v-for

This vue directive is used when you need to render multiple tags of similar content. For example, you can have 10 different dishes for your recipe website and you can display all the 10 one by one.

```vue
<script setup>
const list = ref([1, 2, 3, 4, 5, 6, 7, 8, 9, 10]) // array of numbers
// ...
</script>

<template>
    <!-- code -->
    <div v-for="item in list">
      <p style="color: red;">{{ item }}</p>
    </div>
</template>
```

This allows you to have 10 different `<div />` with numbers from 1 to 10 in red coloured text.

#### v-bind

We learnt that we can inject any reactive state inside the HTML using double curly brackets, `{{ state }}`. However, if we want to inject anything into an HTML *attribute*, we need to use the `v-bind` directive.

```vue
<script setup>
const pColor = ref("red")
// code
</script>

<template>
    <!-- code -->
    <div v-for="item in list" v-bind:key="item">
      <p v-bind:style="{color: pColor}">{{ item }}</p>
    </div>
</template>
```

**Note:** `v-bind:` will accept JavaScript code inside the quotation marks and not the actual string.
The "key" attribute is important while using the `v-for` directive as Vue needs to keep a track of all the elements it is rendering incase of any changes to the reactive list.

We can also shorten the HTML part to:

```vue
<template>
    <!-- code -->
    <div v-for="item in list" :key="item">
      <p :style="{color: pColor}">{{ item }}</p>
    </div>
</template>
```
