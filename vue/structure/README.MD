


### `assets`

The assets directory contains your uncompiled assets such as Stylus or Sass files, images, or fonts.


### `components`

The components directory contains your Vue.js components. Components make up the different parts of your page and can be reused and imported into your pages, layouts and even other components.

### `routes`

This directory contains your router configuration.

### `layouts`

Layouts are a great help when you want to change the look and feel of your  app, whether you want to include a sidebar or have distinct layouts for mobile and desktop.



### `views`

This directory contains your application views and routes.


### `plugins`

The plugins directory contains JavaScript plugins that you want to run before instantiating the root Vue.js Application. This is the place to add Vue plugins and to inject functions or constants. Every time you need to use `Vue.use()`, you should create a file in `plugins/` 


### `public`

This directory contains your static files. Each file inside this directory is mapped to `/`.

Example: `/public/robots.txt` is mapped as `/robots.txt`.


### `store`

This directory contains your Vuex store files.

### `/src/constant.js`

In this file only unchangeable variables should be stored. For example user's roles:
```js
export const USER_ROLES = {
  "ADMIN": "Admin",
  "PARTNER": "Partner",
  "EMPLOYEE": "EMPLOYEE"
}
```

and they can be imported where they are needed.

```vue
...
<script>
  import {USER_ROLES} from './constants.js'
  export default {
    //...
    computed: {
      userRoles() {
        return USER_ROLES
      }
    },
    mounted() {
      if(this.user.role === USER_ROLES['ADMIN']) {
        // some work can be here 
      }
    }
  }
</script>
```


><span style="color: #ff6985">In this file any kind of manipulations, logics and functions mustn't be written.</span>


### `.env`
In this file all of the necessary unchangeable data should be stored.
```
.env                # loaded in all cases
.env.local          # loaded in all cases, ignored by git
.env.[mode]         # only loaded in specified mode
.env.[mode].local   # only loaded in specified mode, ignored by git
```

>Do not store any secrets (such as private API keys) in your app!
Environment variables are embedded into the build, meaning anyone can view them by inspecting your app's files.


####If you are using vue cli:
```dotenv
VUE_APP_BASE_URL=some_value
```
Note that only NODE_ENV, BASE_URL, and variables that start with VUE_APP_ will be statically embedded into the client bundle with webpack.DefinePlugin. It is to avoid accidentally exposing a private key on the machine that could have the same name. ([For more](https://cli.vuejs.org/guide/mode-and-env.html#environment-variables))


####Agar vite ishlatyotgan bo'lsangiz.
Loaded env variables are also exposed to your client source code via import.meta.env.
To prevent accidentally leaking env variables to the client, only variables prefixed with VITE_ are exposed to your Vite-processed code. e.g. the following file:([For more](https://vitejs.dev/guide/env-and-mode.html))
```dotenv
VITE_SOME_KEY=123
```







### `.gitignore example file`

```gitignore
.DS_Store
node_modules
/dist


# local env files
.env.local
.env.*.local

# Log files
npm-debug.log*
yarn-debug.log*
yarn-error.log*
pnpm-debug.log*


# Editor directories and files
.idea
.vscode
*.suo
*.ntvs*
*.njsproj
*.sln
*.sw?

```


