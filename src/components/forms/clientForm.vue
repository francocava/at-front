<template>
  <v-container>
    <v-card>
      <v-card-title>Cliente Nuevo</v-card-title>

      <v-card-text>
        <v-form ref="form" v-model="valid" lazy-validation>
          <!-- Old way replaced by line 18 -->

          <!-- <Name
            :value="form.name"
            @updateName="
              (v) => {
                form.name = v.target.value;
              }
            "
          /> -->
          <Name v-model="form.name" />

          <DNI v-model="form.dni" />

          <Telephone v-model="form.telephone" />

          <SubmitButton :valid="valid" />
        </v-form>
      </v-card-text>
    </v-card>
  </v-container>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import Name from "./nameField.vue";
import DNI from "./dniField.vue";
import Telephone from "./telephoneField.vue";
import SubmitButton from "./SubmitButton.vue";

export default defineComponent({
  name: "ClientForm",
  components: {
    Name,
    DNI,
    Telephone,
    SubmitButton,
  },

  data: () => ({
    snackbar: {
      display: false,
      text: "",
      color: "black",
    },
    valid: true,
    form: {
      name: "",
      dni: "",
      telephone: "",
    },
  }),
});
</script>
