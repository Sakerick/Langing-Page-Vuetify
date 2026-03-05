<template>
  <v-app>
    <v-main>
      <v-container class="d-flex justify-center align-center ga-6">
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/perros">Perros</RouterLink>
      </v-container>
      <router-view />
    </v-main>
  </v-app>
</template>

<script lang="ts" setup>
  //
</script>
