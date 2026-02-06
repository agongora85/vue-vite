<script setup>
  const name="Vue dinámico"
  const stylecolor="color:blue"
  const arrayColores=["blue","red","peru"]
  const arrayfrutas=[
    {
      name:"Manzana",
      price:"$1.00",
      description:"Una manzana",
    },
    {
      name:"Pera",
      price:"$2.00",
      description:"Una pera",
    },
    {
      name:"Naranja",
      price:"$3.00",
      description:"Una naranja",
    },
  ];
  const objetoFruta={
    name:"Manzana",
    price:"$1.00",
    id:1
  };
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
  <ul>
    <li v-for="color in arrayColores">
       {{ color }}
    </li> 
  </ul>
  <ul>
    <li v-for="fruta in arrayfrutas" :key="fruta.name">
      {{ fruta.name }} - {{ fruta.description }} - {{ fruta.price }}
    </li>
  </ul>
  <ul>
    <li v-for="(value, propiedad, index) in objetoFruta":key="value">
      {{ index }} - {{ propiedad }} : {{ value }}
    </li>
  </ul>
</template>
<style>
  h1{
    color:blue;
  }
</style>