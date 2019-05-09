<template>
  <div id="app" class="container">
    <login-form v-if="!login" id="login" class="col-md-3 col-sm-5 col-xs-12"/>
    <home class="home" id="home" v-else />

  </div>
</template>

<script>
// import Cookies from 'js-cookie';
import Vue from 'vue';
import loginForm from './components/login/login-form.vue';
import home from './components/home/home.vue';
import VueResource from "vue-resource";
Vue.use(VueResource);

export default {
  name: 'app',
  components: {
    loginForm,
    home,
  },
  data(){
    return{
      login: true,
    }
  },
  methods: {

  },
}
</script>

<style>
#app {
  width: 100%;
  min-height: 500px;
  background: url('./assets/background.png');
  position: relative;

}

#login {
  display: block;
  position:absolute;
  left:50%;
  transform:translate(-50%);
  margin-top: 5rem;

}

#home {

}

@import "https://cdn.jsdelivr.net/npm/bootstrap@3.3.7/dist/css/bootstrap.min.css";
</style>
