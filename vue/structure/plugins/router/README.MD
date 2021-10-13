# Router plugin settings

- First of all, create a new folder called plugins and inside it create a folder called router and inside this folder create a file index.js and a folder called modules.

* plugins
  - router
    - modules
    - index.js

- Don't write all of your path configurations in only index.js file instead of doing this you can create a new file which is dedicated to only one grouped pathes. Look at this example. As you see, everything related to about page is collected in one file and located inside modules folder.

* plugins
  - router
    - modules
      - aboutRoutes.js
    - index.js

```js
<script>
export const routes = [
{
  path: '/about',
  component: import('/views/About.vue'),
  children: [{
  path: 'about-details',
  component: import('/views/AboutDetails.vue')
  }];
}
]
</script>
```

At the end, all of this kind of files should be imported to index.js file as follows.

```js
<script>
import { routes as aboutRoutes } from "./modules/aboutRoutes.js";
const routes = [...aboutRoutes];

const router = new VueRouter({
  routes,
  mode: "history",
});

export default router;
</script>
```

- If you create nested routes, always write routes' names fully. For example:

```js
<script>
export const routes = [
{
  path: '/about',
  component: import('/views/About.vue'),
  name: 'about',
  children: [{
  path: 'about-news',
  name: 'about-news',
  component: import('/views/AboutNews.vue'),
  children: [{
  path: 'about-news-detailed',
  name: 'about-news-detailed',
  component: import('/views/AboutNewsDetailed.vue')
  }];
  }];
}
]
</script>
```

- Always use slashes appropriately before pathnames. Take following About.vue file and AboutDetails.vue file as an example. In this certain scenario slash isn't used before about-details path because here the main goal is to show AboutDetails.vue file's content when user goes to '/about/about-details'. If slash was used like '/about-details', AboutDetails.vue file's content would be visible when user went to '/about-details' path. For more information click [here](https://router.vuejs.org/guide/essentials/nested-routes.html).

```js
<script>
{
  path: '/about',
  component: import('/views/About.vue'),
  children: [{
  path: 'about-details',
  component: import('/views/AboutDetails.vue')
  }];
}
</script>
```

- All routes should be named by kebab-case.

```js
<script>
export const routes = [
{
  path: '/about',
  name: 'about',
  component: import('/views/About.vue'),
  children: [{
  path: 'about-details',
  name:'about-details',
  component: import('/views/AboutDetails.vue')
  }];
}
]
</script>
```

- If you create dynamic route, don't forget to write props: true and comments which contain the whole path.

```js
<script>
export const routes = [
{
  path: '/about',
  name: 'about',
  component: import('/views/About.vue'),
  children: [{
  path: 'about-details/:id'  // /about/about-details/:id,
  name:'about-details',
  component: import('/views/AboutDetails.vue'),
  props: true
  }];
}
]
</script>
```

- Last but not least, don't forget to import router.js file in your main.js file.

```js
<script>
import Vue from "vue";
import router from ".plugins/router/index.js";

new Vue({
  router,
  render: (h) => h(App),
}).$mount("#app");
</script>
```
