<template>
  <v-container class="d-flex flex-column align-center justify-center">
    <v-row class="w-100 pa-5">
      <v-col cols="6">
        <v-skeleton-loader
          v-if="isLoading"
          height="400"
          type="card, list-item-two-line"
        />
        <CardComp
          v-else
          :author="author1"
          description="Con botón se generará una nueva imagen aleatoria"
          :src="card1Src"
          title="Titulo card 1"
        />
      </v-col>

      <v-col cols="6">
        <v-skeleton-loader
          v-if="isLoading"
          height="400"
          type="card, list-item-two-line"
        />

        <CardComp
          v-else
          :author="author2"
          description="Con botón se generará una nueva imagen aleatoria"
          :src="card2Src"
          title="Titulo card 2"
        />
      </v-col>
    </v-row>

    <v-btn
      class="pa-5 ma-5"
      color="primary"
      :disabled="isLoading"
      :loading="isLoading"
      @click="changeImages()"
    >
      Cambiar imagenes
    </v-btn>

    <v-row class="w-100">
      <v-col cols="12">
        <TableComp />
      </v-col>
    </v-row>
  </v-container>
</template>

<script lang="ts" setup>
  import { onMounted, ref } from 'vue'
  import CardComp from './CardComp.vue'
  import TableComp from './TableComp.vue'

  const card1Src = ref('')
  const card2Src = ref('')
  const author1 = ref('')
  const author2 = ref('')
  const isLoading = ref(false)

  async function changeImages () {
    isLoading.value = true
    try {
      const [img1, img2] = await fetchRandomImages()
      // Asignamos los valores
      card1Src.value = img1.url
      author1.value = img1.author
      card2Src.value = img2.url
      author2.value = img2.author
    } catch (error) {
      console.error(error)
    } finally {
      // Pequeño timeout opcional si la API es demasiado rápida
      // y quieres que el efecto de carga se note.
      setTimeout(() => {
        isLoading.value = false
      }, 500)
    }
  }

  async function fetchRandomImages () {
    const response = await fetch('https://picsum.photos/v2/list?limit=30')
    const data = await response.json()
    const idx1 = Math.floor(Math.random() * data.length)
    let idx2 = Math.floor(Math.random() * data.length)
    while (idx1 === idx2) idx2 = Math.floor(Math.random() * data.length)

    return [
      { url: `https://picsum.photos/id/${data[idx1].id}/400/400`, author: data[idx1].author },
      { url: `https://picsum.photos/id/${data[idx2].id}/400/400`, author: data[idx2].author },
    ]
  }

  onMounted(() => {
    changeImages()
  })
</script>
