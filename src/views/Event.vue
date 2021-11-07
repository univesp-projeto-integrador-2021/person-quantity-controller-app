<template>
  <div class="event">
    <v-app>
      <v-main>
        <div class="search">
          <Input @input.native="filter = $event.target.value" />
        </div>
        <div>
          <Card
            v-for="event in filteredItems"
            :key="event.id"
            :event="event"
          />
        </div>
      </v-main>
    </v-app>
  </div>
</template>

<script>
import Input from "../components/Input.vue";
import Card from "../components/Card.vue";
import axios from "axios";

export default {
  components: {
    Input,
    Card,
  },
  data: () => ({
    events: [],
    filter: ''
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
    availableEvents() {
      return this.events
        .filter((event) => event.available_vacancies > 0)
        .sort((a, b) => (a.name > b.name ? 1 : -1));
    },
    filteredItems() {
      if (this.filter) {
        const events = this.events.filter((event) => {
          return event.name.toLowerCase().includes(this.filter.toLowerCase());
        });
        return events;
      }
      return this.availableEvents;
    },
  },
};
</script>
<style scoped>
.search {
  display: flex;
  margin: 1% 15.5%;
}
.btn {
  margin-left: 30px;
}
</style>
