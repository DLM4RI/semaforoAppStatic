<!-- LOGICA DISEÑADA POR VIPER (Mario Castro) -->
<template>
  <main class="contenedor-principal">
    <careta>
      <Circulo :color_fondo="colorRojo"     :sombra="sombraRojo"     />
      <Circulo :color_fondo="colorAmarillo" :sombra="sombraAmarillo" />
      <Circulo :color_fondo="colorVerde"    :sombra="sombraVerde"    />
    </careta>
  </main>
</template>

<script lang="js" setup>
import { ref, onMounted, onUnmounted } from "vue"
import Circulo from "./components/circulo.vue"


const APAGADO       = "#2a2a2a"
const ROJO_VIVO     = "#ED0000"
const AMARILLO_VIVO = "#FFA400"
const VERDE_VIVO    = "#00EB0C"


const SOMBRA_APAGADA  = "none"
const SOMBRA_ROJA     = "0px 0px 40px #ED0000"
const SOMBRA_AMARILLA = "0px 0px 40px #FFA400"
const SOMBRA_VERDE    = "0px 0px 40px #00EB0C"


const TIEMPO_ROJO     = 10000  
const TIEMPO_AMARILLO = 2000  
const TIEMPO_VERDE    = 5000  


const colorRojo     = ref(ROJO_VIVO)
const colorAmarillo = ref(APAGADO)
const colorVerde    = ref(APAGADO)

const sombraRojo     = ref(SOMBRA_ROJA)
const sombraAmarillo = ref(SOMBRA_APAGADA)
const sombraVerde    = ref(SOMBRA_APAGADA)

let temporizador = null


function ponerRojo() {
  colorRojo.value     = ROJO_VIVO
  colorAmarillo.value = APAGADO
  colorVerde.value    = APAGADO

  sombraRojo.value     = SOMBRA_ROJA
  sombraAmarillo.value = SOMBRA_APAGADA
  sombraVerde.value    = SOMBRA_APAGADA


  temporizador = setTimeout(ponerAmarillo, TIEMPO_ROJO)
}

function ponerAmarillo() {
  colorRojo.value     = APAGADO
  colorAmarillo.value = AMARILLO_VIVO
  colorVerde.value    = APAGADO

  sombraRojo.value     = SOMBRA_APAGADA
  sombraAmarillo.value = SOMBRA_AMARILLA
  sombraVerde.value    = SOMBRA_APAGADA

 
  temporizador = setTimeout(ponerVerde, TIEMPO_AMARILLO)
}

function ponerVerde() {
  colorRojo.value     = APAGADO
  colorAmarillo.value = APAGADO
  colorVerde.value    = VERDE_VIVO

  sombraRojo.value     = SOMBRA_APAGADA
  sombraAmarillo.value = SOMBRA_APAGADA
  sombraVerde.value    = SOMBRA_VERDE


  temporizador = setTimeout(ponerRojo, TIEMPO_VERDE)
}

onMounted(() => {
  ponerRojo()  
})

onUnmounted(() => {
  clearTimeout(temporizador)  
})
</script>

<style>
* {
  padding: 0;
  margin: 0;
  overflow: hidden;
}

body {
  background: linear-gradient(
    164deg,
    rgba(0, 0, 0, 1) 0%,
    rgba(31, 31, 31, 1) 50%,
    rgba(18, 18, 18, 1) 100%
  );
}

.contenedor-principal {
  max-width: 100vw;
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
</style>