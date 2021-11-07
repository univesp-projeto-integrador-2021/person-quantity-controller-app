<template>
  <div id="app">
    <Header />
    <v-app>     
      <main>
        <router-view />
      </main>
    </v-app>
    <Footer />
  </div>
</template>

<script>
import Footer from "./components/Footer.vue";
import Header from "./components/Header.vue";
export default {
  components: { Footer, Header },
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 50px;
}

@media (max-width: 1200px)  
{
  #app {
    width: 2000px;
  }
}
</style>
