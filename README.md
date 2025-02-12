# VueJS Tutorial

A Vue.js Project

## Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build

# build for production and view the bundle analyzer report
npm run build --report

# run unit tests
npm run unit

# run e2e tests
npm run e2e

# run all tests
npm test

```

For detailed explanation on how things work, checkout the [guide](http://vuejs-templates.github.io/webpack/) and [docs for vue-loader](http://vuejs.github.io/vue-loader).

## Getting started

### Softwares use:

-   [MySql Community 5.6](https://dev.mysql.com/downloads/mysql/5.6.html)
-   [MySql Workbench](https://dev.mysql.com/downloads/workbench/?utm_source=tuicool)
-   [Node JS](https://nodejs.org/en/download/)
-   [PostMan](https://www.getpostman.com/apps)
-   Your favorite Code Editor (as for me I use  [VS Code](https://code.visualstudio.com/download))

### Technologies Used

-   [Vue.js](https://vuejs.org/)
-   [Vue Router](https://router.vuejs.org/)
-   [Boostrap-vue](https://bootstrap-vue.js.org/)
-   [Boostrap](https://getbootstrap.com/)
-   [Axios](https://www.npmjs.com/package/axios)

### Let's Get Started

[Build a Basic CRUD App with Vue.js and Node](https://developer.okta.com/blog/2018/02/15/build-crud-app-vuejs-node#create-your-vuejs-app) - Okta

To get your project off the ground quickly you can leverage the scaffolding functionality from [vue-cli](https://github.com/vuejs/vue-cli). For this tutorial, you are going to use the [progressive web app (PWA) template](https://github.com/vuejs-templates/pwa) that includes a handful of features including [webpack](https://github.com/webpack/webpack), [hot reloading](https://vue-loader.vuejs.org/guide/hot-reload.html), CSS extraction, and unit testing. 

To install  `vue-cli`  run:

```bash
$ npm install -g vue-cli
```

Next, you need to initialize your project. When you run the  `vue init`  command just accept all the default values.

```bash
$ vue init pwa my-vue-app-ui
$ cd ./my-vue-app-ui
$ npm install
$ npm run dev

```

Point your favorite browser to  `[http://localhost:8080](http://localhost:8080/)`  and you should see the fruits of your labor:

![](https://lh3.googleusercontent.com/WorUhbJzDvL_Q_5ZuYmJeEouLY7PfXbB5GpL1KTeLOz_jdhavUD_0P8eHmr3gHitp1ikESuAEG8)

### Install Bootstrap

Let’s install  [bootstrap-vue](https://github.com/bootstrap-vue/bootstrap-vue)  so you can take advantage of the various premade  [components](https://getbootstrap.com/docs/4.0/components/)  (plus you can keep the focus on functionality and not on custom CSS):

```bash
$ npm i bootstrap-vue bootstrap
```

To complete the installation, modify  `./src/main.js`  to include  [bootstrap-vue](https://github.com/bootstrap-vue/bootstrap-vue)  and import the required CSS files. Your  `./src/main.js`  file should look like this:

****IMPORTANT:** 	You might have a problem when copying code, you can add `/src` in `.eslintignore`.**

```js
// The Vue build version to load with the `import` command
// (runtime-only or standalone) has been set in webpack.base.conf with an alias.
import Vue from 'vue'
import App from './App'
import router from './router'
import BootstrapVue from 'bootstrap-vue'
import 'bootstrap/dist/css/bootstrap.css'
import 'bootstrap-vue/dist/bootstrap-vue.css'

Vue.use(BootstrapVue)
Vue.config.productionTip  =  false

new Vue({
  el: '#app',
  router,
  template: '<App/>',
  components: { App }
})
```
    
### Adding Router

To your `./src/router/index.js` file, add this code:

```js
//adding this, you can use vue-router to your vue app
Vue.use(Router)

let router = new Router({
  mode: 'history',
  routes: [
    {
      path: '/',
      name: 'Hello',
      component: Hello
    },
  ]
})
```
  
### Customize Your App Layout in Vue

The web app’s layout is located in a component  `./src/App.vue`. You can use the  [router-view](https://router.vuejs.org/en/api/router-view)  component to render the matched component for the given path.

Open `./src/App.vue` and copy/paste the following code.

```html
<template>
	<div id="app">
		<b-navbar toggleable="md" type="dark" variant="info">
			<b-navbar-toggle target="nav_collapse"></b-navbar-toggle>
			<b-navbar-brand to="/">My Vue App</b-navbar-brand>
			<b-collapse is-nav id="nav_collapse">
				<b-navbar-nav>
					<b-nav-item to="/">
						Home
					</b-nav-item>
				</b-navbar-nav>
			</b-collapse>
		</b-navbar>
		<!-- routes will be rendered here -->
		<router-view />
	</div>
</template>
```

Your nav-bar should look like this:

![enter image description here](https://lh3.googleusercontent.com/TrmRTkfM7fSZFpCHuUSJat8fJaZIh-3Yh-MMCV5X6RVi_6JWtyPWZ2K5JAJHOji_xr2d8CppIaI)

### Building Components

[Components](https://vuejs.org/v2/guide/components)  are the building blocks within Vue.js. Each of your pages will be defined in the app as a component. Since the vue-cli webpack template utilizes  [vue-loader](https://github.com/vuejs/vue-loader), your component source files have a convention that separates template, script, and style ([see here](https://github.com/vuejs/vue-loader)).

Now that you’ve added vue-bootstrap, modify  `./src/components/Hello.vue`  to remove the boilerplate links vue-cli generates.

```html
<template>
	<div class="hero">
		<div>
			<h1 class="display-3">Hello World</h1>
			<p class="lead">This is the homepage of your vue app</p>
		</div>
	</div>
</template>

<style>
  .hero {
    height: 90vh;
    display: flex;
    align-items: center;
    justify-content: center;
    text-align: center;
  }
  .hero .lead {
    font-weight: 200;
    font-size: 1.5rem;
  }
</style>
```

Your home should look like this:

![enter image description here](https://lh3.googleusercontent.com/G6DFTByLCblERyCJVDoZV_zJoKEugb3AFo2kDi3C7Rgrzvs3atag6aQP3C01W7LvY4Q-PznwqMA)

> Note: You can customize your style in style tag! if you want your style to be only in that component, you can add `scoped`. `<style scoped>***</style>`

Then, we can add a component so you can test our API to perform CRUD operations on our User Manager.

Create a new file `./src/components/UserManager.vue` and paste the following code:

```html
<template>
  <div class="container-fluid mt-4">
    <h1 class="h1">User Manager</h1>
  </div>
</template>
```

Now, go to your `./src/router/index.js` file so we can navigate to the `UserManager` component.

Your `index.js` file should look like this:

```js
import Vue from 'vue'
import Router from 'vue-router'
import Hello from '@/components/Hello'
import UserManager from '@/components/UserManager'

Vue.use(Router)

export default new Router({
	routes: [
		{
			path: '/',
			name: 'Hello',
			component: Hello
		},
		{
			path: '/user-manager',
			name: 'UserManager',
			component: UserManager,
		}
	]
})
```

Now that we added the `UserManager` in the router, we will add it also in the nav-bar so we can navigate in `UserManager` component.

In our `App.vue` file, we will add a `<b-nav-item>` going to the path `/user-manager`.

```html
<b-nav-item  to="/user-manager">
	User Manager
</b-nav-item>
```

You can now navigate to the `UserManager` component.

![enter image description here](https://lh3.googleusercontent.com/S2DYCYzGSpr1CkMtuHOxa4PWdEEoSNS_uvapiu71w6nWaIccy03rRmLtNbGta64Ty5lsXrBZN0I)

### Completing our UserManager Component

If you don't have my REST API server, you can clone it [here](https://github.com/tr-trainings/node-tutorial).

Using npm, execute this on your terminal

```bash
$ npm install --save axios
```

Once done, create a file in our project root directory named `services`. In the services folder, create a file `./src/api.js` and copy/paste the following code into it: 

```js
import  axios  from  'axios'

export  default () => {
	return  axios.create({
		baseURL:  `http://localhost:8081/api/`
	})
}
```

> Note: You can read the official GItHub repo for Axios [here](https://github.com/axios/axios).

In the same directory, create a file named `userServices` to make a request in our API and get response. Copy/paste the following code into it: 

```js
import  Api  from  './Api'

export  default {
	getUsers () {
		//this will make a get request in 
		//http://localhost:8081/api/user
		return  Api().get('user')
	},
	createUser (user) {
		//this will make a post request in 
		//http://localhost:8081/api/user
		return  Api().post('user', user)
	},
	getUser (id) {
		//this will make a get request in 
		//http://localhost:8081/api/user/:id
		return  Api().get(`user/${id}`)
	},
	updateUser (id, user) {
		//this will make a put request in 
		//http://localhost:8081/api/user/:id
		return  Api().put(`user/${id}`, user)
	},
	deleteUser (id, user) {
		//this will make a put request in 
		//http://localhost:8081/api/user/:id
		return  Api().put(`user/${id}`, user)
	}
}
```

Open `./src/components/UserManager.vue` and copy/paste the following code.

```html
<template>
	<div  class="container-fluid mt-4">
		<h1  class="h1">User Manager</h1>
		<b-alert  :show="loading"  variant="warning">Loading...</b-alert>
		<b-row>
			<b-col>
				<table  class="table table-striped table-hover"  hover>
					<thead>
						<tr>
							<th>ID</th>
							<th>First Name</th>
							<th>Last Name</th>
							<th>&nbsp;</th>
						</tr>
					</thead>
					<tbody>
						<tr  v-for="user  in  users"  :key="user.id">
							<td>{{ user.user_id }}</td>
							<td>{{ user.user_fname }}</td>
							<td>{{ user.user_lname }}</td>
							<td  class="text-right">
								<a  href="#"  @click.prevent="populateUserToEdit(user)">Edit</a> -
								<a  href="#"  @click.prevent="deleteUser(user.user_id)">Delete</a>
							</td>
						</tr>
					</tbody>
				</table>
				</b-col>
				<b-col  lg="3">
					<b-card  :title="(model.user_id  ?  'Edit user ID #'  +  model.user_id  :  'New user')">
						<form  @submit.prevent="saveUser">
							<b-form-group  label="First Name">
								<b-form-input  type="text"  v-model="model.user_fname"></b-form-input>
							</b-form-group>
							<b-form-group  label="Last Name">
								<b-form-input  type="text"  v-model="model.user_lname"></b-form-input>
							</b-form-group>
							<div>
								<b-btn  type="submit"  variant="success">Save user</b-btn>
								<b-btn  v-if="model.user_id  ?  true  :  false"  variant="default"  @click.prevent="clear()">Cancel</b-btn>
							</div>
						</form>
					</b-card>
			</b-col>
		</b-row>
	</div>
</template>

<script>
	import userService from  '../services/userService'
	export default {
		data () {
			return {
				loading:  false,
				users: [],
				model: {},
				displayModel: {},
				updateModel: {},
				deleteModel: {}
			}
		},
		async  created () {
			this.refreshUsers()
		},
		methods: {
			async refreshUsers () {
				this.loading = true
				this.users = (await userService.getUsers()).data.allUser
				this.loading = false
			},
			async populateUserToEdit (user) {
				this.model = Object.assign({}, user)
			},
			async  saveUser () {
				if (this.model.user_id) {
					this.updateModel = {
						user_fname:  this.model.user_fname,
						user_lname:  this.model.user_lname
					}
					await userService.updateUser(this.model.user_id, this.updateModel)
				} else {
					await userService.createUser(this.model)
				}
				this.model = {} // reset form
				await this.refreshUsers()
			},
			async deleteUser (id) {
				if (confirm('Are you sure you want to delete this user?')) {
				this.deleteModel = {
				user_isdel: 1
				}
				// if we are editing a user we deleted, remove it from the form
				await userService.deleteUser(id, this.deleteModel)
				await this.refreshUsers()
				}
			},
			async clear () {
				this.model  = {}
			}
		}
	}
</script>
```

### Listing Users

You’ll use  `userService.getUsers()`  to fetch users from your REST API server. You should refresh the list of users when the component is loaded and after any mutating operation (create, update, or delete).

```js
async refreshUsers () {
	this.loading = true
	this.users = (await userService.getUsers()).data.allUser
	this.loading = false
}
```

### Creating Users

A form is included in the component to save a user. It’s wired up to call  `saveUser()`  when the form is submitted and its inputs are bound to the  `model`  object on the component.

When  `saveUser()`  is called, it will perform either an update or create based on the existence of  `model.id`. This is mostly a shortcut to not have to define two separate forms for creating and updating.

```js
async  saveUser () {
	if (this.model.user_id) {
		this.updateModel = {
			user_fname:  this.model.user_fname,
			user_lname:  this.model.user_lname
		}
		await userService.updateUser(this.model.user_id, this.updateModel)
	} else {
		await userService.createUser(this.model)
	}
	this.model = {} // reset form
	await this.refreshUsers()
}
```

### Updating Posts

When updating a user, you must first load the user into the form. This sets  `model.id`  which will the trigger an update in  `saveUser()`.

```js
async populateUserToEdit (user) {
	this.model = Object.assign({}, user)
}
```

**Important:**  The  `Object.assign()`  call copies the value of the post argument rather than the reference. When dealing with mutation of objects in Vue, you should always set to the value, not reference.

### Deleting Posts

To delete a user simply call  `userService.deleteUser(id, this.deleteModel)`. It’s always good to confirm before delete so let’s throw in a native confirmation alert box to make sure the click was intentional.

```js
async deleteUser (id) {
	if (confirm('Are you sure you want to delete this user?')) {
	this.deleteModel = {
	user_isdel: 1
	}
	// if we are editing a user we deleted, remove it from the form
	await userService.deleteUser(id, this.deleteModel)
	await this.refreshUsers()
	}
}
```

## Test Your Vue.js + Node CRUD App

Make sure both the server and frontend are running.

In your node-tutorial
Terminal #1

```bash
npm run dev
```

In your node-tutorial-ui
Terminal #2

```bash
npm run dev
```

![enter image description here](https://lh3.googleusercontent.com/hnohj0jP9BpmPiXVzvW6LiGp1OHCKbWpF-Zh3Cp5GHY27n_Od4sxi4mNdGzL0HsotvcCweKOmlM)


## Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build

# build for production and view the bundle analyzer report
npm run build --report

# run unit tests
npm run unit

# run e2e tests
npm run e2e

# run all tests
npm test
```

For detailed explanation on how things work, checkout the [guide](http://vuejs-templates.github.io/webpack/) and [docs for vue-loader](http://vuejs.github.io/vue-loader).
