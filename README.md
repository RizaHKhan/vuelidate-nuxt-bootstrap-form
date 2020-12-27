# Authentication Forms

Steps:

## 1. Create a nuxt app

`yarn create nuxt-app <app-name>`
or
`npx create-nuxt-app <app-name>`
or
`npm init nuxt-app <app-name>`

## 2. Install Bootstrap

### Installation

`npm i bootstrap-vue bootstrap`
or
`yarn add bootstrap-vue bootstrap`

### Registration

Create a `bootstrapvue.js` file in the plugins folder.

```
import 'bootstrap/dist/css/bootstrap.css'
import 'bootstrap-vue/dist/bootstrap-vue.css'
import Vue from 'vue'
import BootstrapVue from 'bootstrap-vue' // can also destructure and pull only the components you need

Vue.use(BootstrapVue)

```

And in your `nuxt.config.js` file:

```
  plugins: [
    { src: '@/plugins/bootstrap-vue.js', mode: 'client' },
  ],
```

## 3. Install Vuelidate

### Installation

`npm i vuelidate`

### Registration

Create a `bootstrapvue.js` file in the plugins folder.

```
import Vue from 'vue'
import Vuelidate from 'vuelidate'

Vue.use(Vuelidate)

```

And in your `nuxt.config.js` file:

```
  plugins: [
    { src: '@/plugins/vuelidate', ssr: true },
  ],
```
