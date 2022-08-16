<template>
    <Router-link to="/about">About <i class="fa-solid fa-globe"></i></Router-link>
    <br />
    <img class="image" alt="Vue logo" src="../assets/logo.png">
    <h3>Track your groceries</h3>
    <br />
</template>

<script>
export default {
  name: 'Header',
  
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.image{
  width: 500px;
  height: 200px
}

/* CSS */

</style>
