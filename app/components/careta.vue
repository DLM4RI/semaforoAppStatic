<template>
  <div class="contenedor-rectangulo">
    <slot></slot>
  </div>
</template>

<script lang="js" setup></script>

<style>
.contenedor-rectangulo {
  /* ancho se adapta a la pantalla */
  width: clamp(150px, 30vw, 300px);

  /* alto se adapta a la pantalla */
  height: clamp(300px, 70vh, 600px);

  padding: 5% 0%;
  background-color: rgb(23, 23, 23);
  border-radius: 30px;
  border: 2px solid gray;
  box-shadow: 0px 0px 30px rgba(0, 0, 0, 0.421);

  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  gap: 5%;
}
</style>
