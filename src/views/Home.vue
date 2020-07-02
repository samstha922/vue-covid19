<template>
  <div class="home">
    <h1>Covid19 Tracker</h1>
    <Header :msg ="msg"/>
    <b-container class="bv-example-row">
      <b-row>
        <b-col sm="8"><Statistics></Statistics></b-col>
        <b-col sm="4"><Announcements></Announcements></b-col>
      </b-row>
    </b-container>    
  </div>
</template>
<script>
// @ is an alias to /src
//import HelloWorld from '@/components/HelloWorld.vue'
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
