<template>
  <div 
    class="contenedor-circulo" 
    :style="{ backgroundColor: color_fondo, boxShadow: sombra }"
  ></div>
</template>

<script lang="js" setup>
defineProps({
  color_fondo: String,
  sombra: String,
})
</script>

<style>
.contenedor-circulo {
  width: 65%;
  height: 33%;
  border-radius: 50%;
  transition: background-color 0.4s ease, box-shadow 0.4s ease;
}
</style>