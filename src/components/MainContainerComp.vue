<template>
  <v-container class="d-flex flex-column align-center justify-center">
    <v-row>
      <v-col cols="6">
        <CardComp :blur="false" :src="'https://picsum.photos/600/600/?random=' + Math.floor(Math.random() * 1000)" text="Al cliquear la imagen se generará una nueva imagen aleatoria" />
      </v-col>
      <v-col cols="6">
        <CardComp
          :blur="true"
          :src="'https://picsum.photos/600/600/?blur&random=' + Math.floor(Math.random() * 1000)"
          text="Al cliquear la imagen se generará una nueva imagen con efecto blur aleatoria"
        />
      </v-col>
    </v-row>
    <v-row>
      <v-col cols="12">
        <TableComp />
      </v-col>
    </v-row>
  </v-container>
</template>

<script lang="ts" setup>
  import CardComp from './CardComp.vue'
  import TableComp from './TableComp.vue'
</script>
