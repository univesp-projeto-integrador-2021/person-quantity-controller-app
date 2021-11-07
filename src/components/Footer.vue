<template>
  <v-footer dark padless>
    <v-card-title class="footer">
      <div>
        <ul>
          <p>Eventos</p>
          <li><router-link to="/events" class="event-btn"> Encontre um evento</router-link></li>
        </ul>
      </div>
      <v-spacer></v-spacer>

      <div class="social">
        <p class="ml-1">Siga-nos</p>
        <v-btn v-for="icon in icons" :key="icon" class="mr-2" dark icon>
          <v-icon size="30px">
            {{ icon }}
          </v-icon>
        </v-btn>
      </div>
    </v-card-title>
  </v-footer>
</template>

<script>
export default {
  data: () => ({
    icons: ["mdi-facebook", "mdi-twitter", "mdi-youtube", "mdi-instagram"],
  }),
};
</script>
<style>
* {
  font-family: Roboto;
}
.footer {
  width: 100%;
  height: 156px;
  background: #24284e;
}

ul {
  list-style: none;
  margin-left: 60px !important ;
}
ul p {
  font-size: 18px;
}
li {
  font-size: 14px;
}

.social {
  font-size: 14px;
  margin-right: 60px;

}
.event-btn {
  text-decoration: underline;
  cursor: pointer;
  color: #fff;
}
</style>