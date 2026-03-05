<template>
  <v-card class="ma-auto pa-auto">
    <v-img :src="src" />
    <v-card-title> {{ props.title }}
    </v-card-title>
    <v-card-text>
      {{ props.description }}
    </v-card-text>
    <v-card-subtitle>
      Autor: {{ props.author }}
    </v-card-subtitle>
  </v-card>
</template>

<script lang="ts" setup>
  const props = defineProps({
    src: {
      type: String,
      required: true,
    },
    title: {
      type: String,
      required: true,
    },
    description: {
      type: String,
      required: true,
    },
    author: {
      type: String,
      required: true,
    },
  })
</script>
