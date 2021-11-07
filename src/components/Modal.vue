<template>
  <div>
    <template>
      <v-row justify="center">
        <v-dialog
          v-model="dialog"
          persistent
          class="modal_container"
          max-width="600px"
        >
          <v-card>
            <div>
              <img src="../assets/logo.svg" alt="logo" class="logo-img" />
            </div>
            <div>
              <img
                src="../assets/close.svg"
                alt="logo"
                class="close-img"
                @click="dialog = false"
              />
            </div>
            <v-card-text>
              <v-container>
                <v-row>
                  <v-card-title>
                    <h2>Participe do evento:</h2>
                    <h1 class="mt-3 font-weight-black black--text d-block">
                      {{ event.name }}
                    </h1>
                  </v-card-title>
                  <v-col cols="12">
                    <v-form ref="form" v-model="valid" lazy-validation>
                      <v-col cols="12">
                        <v-text-field
                          v-model="form.person_name"
                          :rules="nameRules"
                          label="Nome Completo"
                          type="text"
                          required
                        ></v-text-field>
                      </v-col>
                      <v-col cols="12">
                        <v-text-field
                          v-model="form.email"
                          :rules="emailRules"
                          label="Email"
                          required
                        ></v-text-field>
                      </v-col>
                      <v-col cols="12">
                        <v-text-field
                          v-model="form.nickname"
                          :rules="nicknameRules"
                          label="Apelido"
                          type="text"
                          required
                        ></v-text-field>
                      </v-col>
                    </v-form>
                  </v-col>
                </v-row>
              </v-container>
            </v-card-text>
            <v-card-actions>
              <v-spacer></v-spacer>
              <v-btn color="blue darken-1" text @click="saveUser">
                Salvar
              </v-btn>
            </v-card-actions>
          </v-card>
        </v-dialog>
        <div @click="dialog = true">
          <Button buttonName="Participar"/>
        </div>
          <Snackbar :snackbar="snackbar" />
      </v-row>
    </template>
  </div>
</template>

<script>
import axios from "axios";
import Button from "../components/Button.vue";
import Snackbar from "./Snackbar.vue";

export default {
  props: {
    event: {
      type: Object,
    },
  },
  components: {
    Button,
    Snackbar,
  },
  data: () => ({
    dialog: false,
    valid: true,
    snackbar: {
      show: false,
      message: null,
      color: null,
    },
    nameRules: [
      (v) => !!v || "Por favor insira um nome",
      (v) => (v && v.length >= 10) || "O Nome deve ter mais que 10 caracteres",
    ],
    emailRules: [
      (v) => !!v || " Por favor insira um e-mail",
      (v) => /.+@.+/.test(v) || "O e-mail não é válido!",
    ],
    nicknameRules: [
      (v) => !!v || "Por favor insira um apelido",
      (v) => (v && v.length >= 2) || "o apelido deve ter mais que 2 caracteres",
    ],
    form: {
      person_name: "",
      nickname: "",
      email: "",
    },
  }),
  computed: {},
  methods: {
    async saveUser() {
      if (this.$refs.form.validate()) {
        try {
          await axios.post("http://localhost:3030/appointment", {
            ...this.form,
            event: this.event,
          });
          this.snackbar = {
            show: true,
            message: `Parabéns! Sua inscrição foi realizada com sucesso.`,
            color: "success",
          };
          return this.event.available_vacancies--;
        } catch (e) {
          console.log(e);
          return this.snackbar = {
            show: true,
            message: `Ocorreu um erro ao se cadastrar no evento: ${e.message}`,
            color: "error",
          };
        } finally {
          this.dialog = false;
        }
      }
    },
  },
};
</script>

<style scoped>
.logo-img {
  width: 80px;
  margin: 10px 0 0 30px;
}

.close-img {
  position: absolute;
  right: 30px;
  top: 30px;
  cursor: pointer;
}

.modal_container {
  height: 100px !important;
}

.v-card__title {
  display: block !important;
}
</style>
