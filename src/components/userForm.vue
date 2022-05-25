<template>
  <div>
    <v-card>
      <v-card-title>Usuario Nuevo</v-card-title>

      <v-card-text>
        <v-form ref="form" v-model="valid" lazy-validation>
          <Name />

          <v-text-field
            type="number"
            v-model="pass"
            label="Constraseña"
            :rules="passRules"
          ></v-text-field>

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
import Name from "./nameForm.vue";

export default defineComponent({
  components: {
    Name,
  },

  data: () => ({
    snackbar: {
      display: false,
      text: "",
      color: "black",
    },

    roles : ["Admin","Empleado"],

    valid: true,
    form: {
      nombre: "",
      pass: "",
      role: ""
    },
    passRules: [(v) => !!v || "Falta la constraseña del Usuario"],
  }),
});
</script>
