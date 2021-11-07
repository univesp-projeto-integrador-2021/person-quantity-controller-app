<template>
  <v-card>
    <div class="container">
      <div class="div-img">
        <img
          :src="
            event.image ||
              'https://www.generationsforpeace.org/wp-content/uploads/2018/03/empty.jpg'
          "
          alt="imagem do evento"
          class="img-event"
        />
      </div>
      <div class="information">
        <h3>{{ event.name }}</h3>
        <p>{{ event.day }} - {{ event.start_date_time }}</p>
        <p v-if="event.description">{{ event.description }}</p>
        <p>
          {{ location.street }}, {{ location.house_number }},
          {{ location.neighborhood }}, {{ location.state }} -
          {{ location.city }}
        </p>
        <h4>{{ event.available_vacancies }} vagas disponíveis</h4>
      </div>
         <Modal class="btn-event" :event="event" />
    </div>
  </v-card>
</template>

<script>
import Modal from './Modal.vue';
export default {
  props: ["event"],
  data: () =>({
  }),
    methods: {
  },
  computed: {
    location() {
      return this.event.location;
    },

  },
  components: {  Modal },

};
</script>

<style scoped>
.container {
  width: 100%;
  height: 200px;
  margin-left: 15.5%;
  display: flex;
  align-items: center;
  justify-content: flex-start;
}

.img-event {
  height: 118px;
  width: 177px;
  border-radius: 8px;
}
.div-img {
  margin-right: 20px;
}
.information p {
  margin-bottom: 5px !important;
  color: #5b5858;
  max-width: 400px;
}
.btn-event {
  margin-top: 100px;
}
</style>
