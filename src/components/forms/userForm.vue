<template>
  <div>
    <v-card>
      <v-card-title>Usuario Nuevo</v-card-title>

      <v-card-text>
        <v-form ref="form" v-model="valid" lazy-validation>
          <Name />

          <Password />

          <v-select
            v-model="form.role"
            :items="roles"
            item-value="id"
            item-text="nombre"
            :rules="[(v) => !!v || 'Ingresar rol']"
            label="Rol"
            required
          ></v-select>

          <v-btn
            :disabled="!valid"
            color="success"
            class="mr-4"
            @click="validate"
          >
            Enviar
          </v-btn>
        </v-form>
      </v-card-text>
    </v-card>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import Name from "./nameField.vue";
import SubmitButton from "./submitButton.vue";
import Password from "./passwordField.vue";

export default defineComponent({
  name: "UserForm",
  components: {
    Name,
    SubmitButton,
    Password,
  },

  data: () => ({
    snackbar: {
      display: false,
      text: "",
      color: "black",
    },

    roles: ["Admin", "Empleado"],

    valid: true,
    form: {
      nombre: "",
      pass: "",
      role: "",
    },
    passRules: [(v) => !!v || "Falta la constraseña del Usuario"],
  }),
});
</script>
