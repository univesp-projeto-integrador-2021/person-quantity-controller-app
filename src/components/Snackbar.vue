<template>
  <v-snackbar
    class="snackbar"
    v-model="snackbar.show"
    :timeout="5000"
    :color="snackbar.color"
    top
    right
  >
    {{ snackbar.message }}
  </v-snackbar>
</template>

<script>
export default {
  props: ["snackbar"],
  data: () => ({
    snackbar: {
      color: null,
      message: "",
      show: false,
    },
  }),
  methods: {},
};
</script>

<style>
.snackbar {
  font-weight: bold;
  text-align: center;
}
</style>