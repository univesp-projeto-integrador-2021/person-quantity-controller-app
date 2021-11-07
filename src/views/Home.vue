<template>
  <div class="home__container">
    <div class="home">
      <div>
        <h1>Cadastre-se em eventos na nossa plataforma</h1>
        <p>
          Aqui na <strong>SGRRP</strong> você participa dos seus eventos de uma
          forma bem mais controlada e inovadora.
        </p>
      </div>
      <div class="circle"></div>
      <div class="circle2"></div>
      <img src="../assets/img_home.svg" alt="imagem" />
    </div>
    <carousels />
  </div>
</template>

<script>
import Carousels from "../components/Carousels.vue";

export default {
  components: { Carousels },
  name: "Home",
};
</script>

<style scoped>
.home__container {
  display: flex;
  flex-direction: column;
  align-content: space-between;
  justify-content: space-between;
  height: 100vh;
  margin-bottom: 5%;
}

h1 {
  height: 112px;
  width: 521px;
  font-size: 48px;
  margin: 50px 0 35px 60px;
}
p {
  height: 84px;
  width: 343px;
  font-size: 18px;
  font-weight: 400;
  color: #8b8b8b;
  margin-left: 65px;
  margin-top: 8%;
}
.circle {
  position: absolute;
  top: 1.5rem;
  right: -2.5rem;
  width: 580px;
  height: 610px;
  border-radius: 50%;
  background: rgba(249, 108, 108, 0.103);
}
.circle2 {
  position: absolute;
  top: 1.5rem;
  right: -2.5rem;
  width: 450px;
  height: 475px;
  border-radius: 50%;
  background: rgba(247, 218, 175, 0.253);
}
img {
  position: absolute;
  top: 7.5rem;
  left: 50%;
}
.search {
  display: flex;
  margin: 150px 60px;
}
.btn {
  margin-left: 30px;
}
</style>
