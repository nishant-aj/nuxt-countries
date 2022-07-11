# Building the Components

## Table of Contents

- [Adding meta data](#adding-meta-data)
- [Creating Components](#creating-components)

## Adding meta data

Now usually we write the `<link />` and the `<script />` tags inside the `<head />` on an HTML file. 
But here we don't have any HTML file, so where do we add it?
We add it in our [nuxt.config.ts](./nuxt.config.ts) file.

```ts
export default defineNuxtConfig({
  meta: {
    link: [
      {
        rel: 'stylesheet',
        href: 'https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css'
      },
      {
        rel: 'stylesheet',
        href: 'https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.1.1/css/all.min.css'  
      }
    ],
    script: [{
      src: 'https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/js/bootstrap.bundle.min.js'
    }]
  }
})
```

With this configuration, we have added [Bootstrap](https://getbootstrap.com/) and [FontAwesome](https://fontawesome.com/) to our project.

## Creating Components

Our websites are built using several different components working together directly or indirectly.
We shall start off by creating our first component.
We must create a folder in the root directory of the project, `components/`.
Inside this folder, let's create a *.vue* file, [Nav.vue](./components/Nav.vue). This shall be the code for the Nav bar on the top.
View the code to understand the navigation bar is coded.

Similarly, we will also code the Search bar and the Card. **Note** that `Search.vue` is inside the `components/` folder while `Card.vue` is inside the `components/country` folder. Hence, while referencing the components, we will also include the folder name in the tag as well.

Check out [app.vue](./app.vue) to see how we call the components and use them inside the website.
