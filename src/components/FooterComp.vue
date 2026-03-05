<template>
  <v-footer class="d-flex text-center pa-4" dark>
    <v-row>
      <v-col>
        Herick Gerardo Vizcarra Macias
      </v-col>
    </v-row>
    <v-row>
      <v-col>
        1190154
      </v-col>
    </v-row>
    <v-row>
      <v-col>
        {{ obtenerFecha() }}
      </v-col>
    </v-row>
    <v-row>
      <v-col>
        Correo de contacto: herick.vizcarra@uabc.edu.mx
      </v-col>
    </v-row>
  </v-footer>
</template>

<script lang="ts" setup>
  function obtenerFecha () {
    const fecha = new Date()
    return fecha.toLocaleDateString()
  }

</script>
