<template>
  <div>
    <v-tabs class="carousels" height="300px" width="300px">
      <div
        class="image-resource"
        v-for="event in filteredEvents"
        :key="event"
        :event="event"
      >
        <img
          :src="
            event.image ||
            'https://www.generationsforpeace.org/wp-content/uploads/2018/03/empty.jpg'
          "
          alt="imagem do evento"
          class="img-event"
          @click="$router.push('/events')"
        />
        <h1 @click="$router.push('/events')">{{ event.name }}</h1>
      </div>
    </v-tabs>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data: () => ({
    events: [],
  }),
  async mounted() {
    await this.loadEvents();
  },
  methods: {
    async loadEvents() {
      const response = await axios.get("http://localhost:3030/event");
      this.events = response.data;
    },
  },
  computed: {
    filteredEvents() {
      return this.events
        .filter((event) => event.available_vacancies > 0)
        .sort((a, b) => (a.name > b.name ? 1 : -1));
    },
  },
};
</script>

<style scoped>
.image-resource {
  width: 60%;
  padding: 5px 20px;
}

.image-resource img {
  width: 90%;
  height: 80%;
  border-radius: 8px;
  cursor: pointer;
}
.image-resource h1 {
  cursor: pointer;
  color: #353535;
  font-size: 26px;
;
}
</style>
