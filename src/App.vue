<script setup lang="ts">
import { RouterLink, RouterView,} from "vue-router";
import { ref } from 'vue';
import { useTheme } from 'vuetify'

const theme = ref(false);
const themeStyle = useTheme();

function changeTheme() {
  theme.value = !theme.value;
  
  themeStyle.global.name.value = theme.value ? "dark" : "light";
}

</script>

<template>
  <v-app>
    <v-toolbar density="compact">
      <v-app-bar-nav-icon></v-app-bar-nav-icon>

      <v-toolbar-title>
        <router-link to="/"> Vuetify </router-link>
      </v-toolbar-title>

      <v-spacer></v-spacer>

      <v-btn icon @click="changeTheme">
        <v-icon :icon="theme ? 'mdi-weather-night' : 'mdi-weather-sunny'"></v-icon>
      </v-btn>

      <v-btn icon>
        <v-badge content="6" size="x-small" color="red-darken-2">
        <v-icon icon="mdi-bell" color="blue-darken-4"></v-icon>
      </v-badge>
      </v-btn>

      <v-btn
        to="/login"
        variant="outlined"
        color="pink-darken-4"
        size="small"
        text="Login"
      >
      </v-btn>
    </v-toolbar>
    <v-main>
      <v-fade-transition >
        <RouterView />
      </v-fade-transition>
    </v-main>
  </v-app>
</template>
