<template>
  <v-app-bar app color="#fff">
    <div class="d-flex align-center">
      <v-img
        @click="$router.push('/')"
        alt="Vuetify Logo"
        class="logo-img"
        contain
        src="../assets/logo.svg"
        transition="scale-transition"
        width="60"
      />
    </div>
    <v-spacer></v-spacer>
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/events">Eventos</router-link>
    </div>

    <v-spacer></v-spacer>

    <v-btn @click="$router.push('/')" text> 
      <span class="mr-2"></span>
      <v-img width="15" src="../assets/return.svg" />
    </v-btn>
  </v-app-bar>
</template>

<script>
export default {};
</script>

<style lang="scss">
#nav {
  padding: 5px;
  margin: 0px 0 0 0;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #fc8a4a;
    }
  }
}
.logo-img{
  cursor: pointer;
}
</style>