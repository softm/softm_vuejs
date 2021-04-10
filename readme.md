### # vuejs
 - SPA ( Single Page Application )
 - Front End Framework
   - React, Vue.js, Angular
 - 개발자의품격 강의
   - https://www.youtube.com/watch?v=sqH0u8wN4Rs

 - 컴포넌트기반의 SPA를 구축

#### # 컴포넌트(Component)
 - 재사용가능한 UI적인 기본요소
 
#### # SPA(Single Page Application)
 - 단일페이지 어플리케이션
 - 하나의 페이지 안에서 필요한 영역 부분만 로딩.
 - 빠른 페이지 변환
 - 적은 트래픽 양

#### # VUE cli : https://github.com/vuejs/vue-cli/tree/v2#vue-cli--
 - ```npm install -g npx```
 - ```npm install --global yarn```
 - ```npm install -g vue```
 - ```npm install -g @vue/cli``` or ```npm install -g @vue/cli```
 - ```vue install wepack test```

#### # vue 기본 프로젝트 생성
 - ```vue create test```
 - ```npm run serve````
 - http://localhost:8080/

#### # vue router 
 - ```npm install vue-router```
 - https://router.vuejs.org/kr/installation.html

#### # Vue Bootstrap
 - https://bootstrap-vue.org/
 - 

#### # Vue Lifecycle 
 - https://vuejs.org/v2/guide/instance.html#Lifecycle-Diagram

#### # main.js
```js
import Vue from 'vue'
import App from './App.vue'
import { BootstrapVue, IconsPlugin } from 'bootstrap-vue'
import router from "./router";

// Import Bootstrap an BootstrapVue CSS files (order is important)
import 'bootstrap/dist/css/bootstrap.css'
import 'bootstrap-vue/dist/bootstrap-vue.css'

Vue.config.productionTip = false
// Make BootstrapVue available throughout your project
Vue.use(BootstrapVue)
// Optionally install the BootstrapVue icon components plugin
Vue.use(IconsPlugin)

new Vue({
  router,
  render: h => h(App),
}).$mount('#app')
```
#### # router.js
```js
import Vue from "vue";
import VueRouter from "vue-router";
import Home from "./views/Home";
import About from "./views/About";

Vue.use(VueRouter);
const router = new VueRouter({
    mode:"history",
    routes:[
        {path:"/",component:Home},
        {path:"/about",component:About},
    ]
});
export default router;
```
#### # App.vue
```js
<template>
  <div id="app">
    <Header/>
    <div id="content" class="content">
      <router-view></router-view>
    </div>
  </div>
</template>

<script>
import Header from './components/layout/Heaer.vue'

export default {
  name: 'App',
  components: {
    Header,
  }
}
</script>
```
#### # Header.vue
```js
<template>
<div>
  <b-navbar toggleable="lg" type="dark" variant="info">
    <b-navbar-brand href="#">NavBar</b-navbar-brand>

    <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

    <b-collapse id="nav-collapse" is-nav>
      <b-navbar-nav>
        <b-nav-item href="#">Link</b-nav-item>
        <b-nav-item href="#" disabled>Disabled</b-nav-item>
      </b-navbar-nav>

      <!-- Right aligned nav items -->
      <b-navbar-nav class="ml-auto">
        <b-nav-form>
          <b-form-input size="sm" class="mr-sm-2" placeholder="Search"></b-form-input>
          <b-button size="sm" class="my-2 my-sm-0" type="submit">Search</b-button>
        </b-nav-form>

        <b-nav-item-dropdown text="Lang" right>
          <b-dropdown-item href="#">EN</b-dropdown-item>
          <b-dropdown-item href="#">ES</b-dropdown-item>
          <b-dropdown-item href="#">RU</b-dropdown-item>
          <b-dropdown-item href="#">FA</b-dropdown-item>
        </b-nav-item-dropdown>

        <b-nav-item-dropdown right>
          <!-- Using 'button-content' slot -->
          <template #button-content>
            <em>User</em>
          </template>
          <b-dropdown-item href="#">Profile</b-dropdown-item>
          <b-dropdown-item href="#">Sign Out</b-dropdown-item>
        </b-nav-item-dropdown>
      </b-navbar-nav>
    </b-collapse>
  </b-navbar>
</div>
</template>

<script>
export default {
    name : "header"
};
</script>

```


#### # Home.vue
```js
<template>
    <div>
        <h1>{{mainTitle}} to {{title}}</h1>
        <input type="text" v-model="input1"/>
        <button type="button" @click="getValue">get</button>
        <button type="button" @click="setValue">set</button>
        <select class="form-control" v-model="region" @change="changeRegion"> 
            <option :key="i" :value="d.v" v-for="(d,i) in regions" >{{d.t}}</option>
        </select>
        <table class="table table-borderd" v-show="tableShow">
        <!-- <table class="table table-borderd" v-if="tableShow"> -->
            <tr :key="i" v-for="(d, i) in regions">
            <td>{{d.v}}</td>
            <td>{{d.t}}</td>
            </tr>
        </table>
    </div>
</template>
<script>
export default {
    data() {
        return {
            mainTitle : "Welcome",
            title : "개발자의 품격",
            input1: "입력값.",
            regions:[
                {v:"S",t:"Seoul"}
              , {v:"J",t:"Jeju"}
              , {v:"B",t:"Busan"}
            ],
            region:"S",
            tableShow : true
        }
    },
    watch: {
        input1() {
            console.log(this.input1);
            //alert("변경됨");
        },
        region() {
            console.log(this.region);
            //alert("변경됨");
        }
    },
    methods: {
        getValue() {
            alert( this.input1 );
        },
        setValue() {
            this.input1  = "1234";
        },
        changeRegion() {
            alert(this.region);
        }
    },
    beforeCreate() {
        // console.log("beforeCreate");
    },
    created() {
        // console.log("created");
    },
    beforeMount() {
        // console.log("beforeMount");
    },
    mounted() {
        // console.log("mounted");
    },
    beforeUpdate() {
        // console.log("beforeUpdate");
    },
    updated() {
        // console.log("updated");
    },
    beforeDestroy() {
        // console.log("beforeDestroy");
    },
    destroyed() {
        // console.log("destroyed");
    },
    name:"Home"
};
</script>
```
#### # About.vue
```js
<template>
    <div>
        <h1>About</h1>
    </div>
</template>
<script>
export default {
    name:"About"
};
</script>

```