<script setup lang="ts">
import { ref } from "vue";

const form = ref({
  email: "",
  password: "",
  remember: "false",
});

const isLoading = ref(false);

const colorRed = "red-darken-1";

function submit() {
  isLoading.value = true;

  setTimeout(() => {
    isLoading.value = false;
    alert(JSON.stringify(form.value));
  }, 2000);
}
</script>

<template>
  <v-container fluid>
    <v-overlay></v-overlay>
    <v-row justify="center">
      <v-col cols="5">
        <v-card class="pa-8" width="300">
          <v-card-title class="text-center">Login here</v-card-title>
          <v-card-item>
            <v-sheet>
              <v-form @submit.prevent="submit">
                <v-text-field
                  variant="solo"
                  prepend-inner-icon="mdi-mail"
                  v-model="form.email"
                  label="Email"
                ></v-text-field>

                <v-text-field
                  variant="solo"
                  prepend-inner-icon="mdi-key"
                  v-model="form.password"
                  label="Password"
                  type="password"
                ></v-text-field>

                <v-checkbox
                  v-model="form.remember"
                  color="red"
                  label="Remember me"
                  hide-details
                ></v-checkbox>

                <v-btn :color="colorRed" class="mt-2" type="submit" block>
                  <v-progress-circular v-if="isLoading"
                    color="white"
                    indeterminate
                  ></v-progress-circular>
                  <span v-else>Submit</span>
                </v-btn>
              </v-form>
            </v-sheet>
          </v-card-item>
          <v-card-action>
            <div class="mx-4">
              <v-btn block to="/register">Register</v-btn>
            </div>
          </v-card-action>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>
