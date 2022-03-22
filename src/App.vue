<template>
 <div id="app">
     <Navbar />
        <div class="container">
<router-view/>
        </div>
        </div>
  <Footer/>
</template>


<script>
import Footer from './components/Footer.vue'
import Navbar from './components/Navbar.vue'
export default {
  components: { Navbar, Footer },
 
}
</script>
<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  background-color: #eee;
  background-image:url("https://i.postimg.cc/4yLjxLHt/wine-4931923-340.jpg")
}
.error-feedback{
  color: rgb(161, 38, 38);
}
</style>
