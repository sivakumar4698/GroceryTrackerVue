<template>
  <Header />
  <div>
 <button v-show = "homePage"
 @click="ToggleAdd" :class= "ShowAdd ? 'fa-solid fa-minus' :'fa-solid fa-plus' "></button>
  </div>
  <br />
   <Router-view :ShowAdd="ShowAdd"></Router-view>
</template>

<script>
import Header from './components/Header.vue'


export default {
  name: 'App',
  components: {
    Header
},
computed: {
  homePage() {
    if(this.$route.path === '/'){
      return true
    }
    else {
      return false
    }
  }
},

  data() {
    return {
      ShowAdd : false
    }
    
  },

  methods: {
   
    ToggleAdd() {
      this.ShowAdd = !this.ShowAdd
    }

}
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

Things Learned 

User Generator Mini Project using the CDN
Vue CLI Setup
Global Styles
29:06 - Header Component
30:44 - Component Props
32:06 - Button Component
35:25 - Events
36:09 - Task Data & created() Method
38:22 - Tasks Component & v-for Loop
41:09 - Single Task Component
44:34 - Dynamic Classes
45:53 - Emit Events (Delete Task)
52:14 - Toggle Reminder
56:20 - AddTask Component & v-model
1:04:57 - Toggle Form & Template Conditionals
1:11:20 - Building For Production
1:13:33 - JSON-Server Setup
1:17:18 - Refactoring to Use The Backend
1:30:48 - Implementing the Router
1:48:23 - Restrict a Component to a Route