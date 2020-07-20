// All the template have to be looked into
<template>
  <div class="home">
    <h1>Covid19 Tracker</h1>
    <Header :msg ="msg"/>
    <b-container class="bv-example-row">
      <b-row>
        <b-col sm="12"><Statistics></Statistics></b-col>
      </b-row>
      <hr>
      <b-row>
        <b-col sm="12"><Announcements></Announcements></b-col>
      </b-row>
    </b-container>  
  </div>
</template>

<script>
// @ is an alias to /src
//import HelloWorld from '@/components/HelloWorld.vue'
import Vue from 'vue'
import { BootstrapVue, IconsPlugin } from 'bootstrap-vue'
// Install BootstrapVue
Vue.use(BootstrapVue)
// Optionally install the BootstrapVue icon components plugin
Vue.use(IconsPlugin)
import 'bootstrap/dist/css/bootstrap.css'
import 'bootstrap-vue/dist/bootstrap-vue.css'
import Header from '@/components/Header.vue'
import Statistics from '@/components/Statistics.vue'
import Announcements from '@/components/Announcements.vue'

export default {
  name: 'Home',
  components: {
    Header,
    Statistics,
    Announcements
    // HelloWorld
  },
  data(){
    return{
      msg:'sam'
    }
  }
}
</script>
