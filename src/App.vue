<script setup>
  const name="Vue dinámico"
  const stylecolor="color:blue"
  const arrayColores=["blue","red","peru"]
  const activo=true
</script>
<template>
  <h1>Hola vue js {{ name.toUpperCase() }}</h1>
  <h2>{{ arrayColores }}</h2>
  <h2 :style='stylecolor'>Soy azul</h2>
  <h2 :style="`color:${arrayColores[2]}`">Soy Perú</h2>
  <h3>{{ activo ? "Estoy activo" : "Estoy inactivo" }}</h3>
  <h4 v-if="activo">
    Me encuentro activo
    <span>Icono</span>
  </h4>
  <h4 v-else>Me encuentro inactivo</h4>
  <h4 v-if="activo === true">Estoy activo</h4>
  <h4 v-else-if="activo === false">Estoy inactivo</h4>
  <p v-else>Estoy inactivo</p>
  <h2 v-show="activo">Estoy activo</h2>
</template>
<style>
  h1{
    color:blue;
  }
</style>