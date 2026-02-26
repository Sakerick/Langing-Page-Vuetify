<template>
  <v-card @click="handleClick">
    <v-img :src="src" />
    <v-card-text>
      {{ props.text }}
    </v-card-text>
  </v-card>
</template>

<script lang="ts" setup>
  import { ref } from 'vue'
  const props = defineProps({
    src: {
      type: String,
      required: true,
    },
    text: {
      type: String,
      required: true,
    },
    blur: {
      type: Boolean,
      required: true,
    },
  })

  // helper to generate a picsum URL with/without blur
  function makeUrl (blur: boolean) {
    const base = 'https://picsum.photos/600/600/'
    // note the proper separator between blur and random
    return blur
      ? `${base}?blur&random=${Math.floor(Math.random() * 1000)}`
      : `${base}?random=${Math.floor(Math.random() * 1000)}`
  }

  const src = ref(props.src)

  function handleClick () {
    // pass the raw boolean prop, not the ref object
    src.value = makeUrl(props.blur)
    console.log('Image changed to:', src.value)
  }
</script>
