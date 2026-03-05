<template>
  <HeaderComp />
  <v-container class="d-flex flex-column align-center justify-center" style="min-height: 75vh;">
    <v-img
      class="rounded-lg elevation-2 bg-grey-lighten-2 mb-4"
      cover
      :height="200"
      :src="imgUrl"
      :width="400"
    >
      <template v-slot:placeholder>
        <div class="d-flex align-center justify-center fill-height">
          <v-progress-circular
            color="primary"
            indeterminate
          />
        </div>
      </template>
    </v-img>

    <v-btn
      color="secondary"
      elevation="2"
      @click="cambiarPerro"
    >
      ¡Otro perrito!
    </v-btn>

  </v-container>
  <FooterComp />
</template>

<script lang="ts" setup>
  import { onMounted, ref } from 'vue'
  import FooterComp from '@/components/FooterComp.vue'
  import HeaderComp from '@/components/HeaderComp.vue'

  const imgUrl = ref('')

  async function cambiarPerro () {
    // Al resetear el imgUrl, Vuetify vuelve a mostrar el placeholder
    imgUrl.value = ''
    try {
      const response = await fetch('https://dog.ceo/api/breeds/image/random')
      const data = await response.json()
      imgUrl.value = data.message
    } catch (error) {
      console.error('Error al obtener el perro:', error)
    }
  }

  onMounted(() => {
    cambiarPerro()
  })
</script>
<style scoped>
.image-frame {
  width: 400px;  /* Ancho fijo */
  height: 200px; /* Alto fijo */
  overflow: hidden;
  border-radius: 8px;
  background-color: #f0f0f0; /* Color de fondo mientras carga */
  display: flex;
  align-items: center;
  justify-content: center;
}

.fixed-img {
  width: 100%;
  height: 100%;
  /* La magia está aquí: recorta la imagen para llenar el espacio sin estirarse */
  object-fit: cover;
}
</style>
