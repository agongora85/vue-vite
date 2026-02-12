<script setup>
  import {ref, computed} from 'vue';
  import headert from "./components/header.vue";
  import headerp from "./components/headerprincipal.vue";
  import footerp from "./components/footer.vue";
  import Lf from "./components/Link-Footer.vue";
  import Navar from "./components/Nav.vue";
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
  const handleClick=(param)=>{
    console.log("El parametro es"+param)
  }
  //Con ref definimos que la variable sea reactiva. Utilizando ref podemos transformar la variable a const en lugar de let
  const counter=ref(0);
  const increment=()=>{
    console.log('aumentar contador');
    counter.value+=1;
  }
  const decrement=()=>{
    counter.value-=1;
  }
  const reset=()=>(counter.value=0)
  const classCounter=computed(()=>{
    if(counter.value===0){
      return 'zero'
    }
    if(counter.value>0){
      return 'positive'
    }

    if(counter.value<0){
      return 'negative'
    }
  })

  //Agregamos un array y lo definimos vacio para luego utilizar la función de push e ir agregando cada elemento que tenemos en variable counter
  //Tener en cuenta que se define como reactivo para poder visualizarlo en la página de forma inmediata
  const arrayFavoritos=ref([]);
  const add=()=>{
    arrayFavoritos.value.push(counter.value)
  }

  const bloquearBtnAdd=computed(()=>{
    const numSearch=arrayFavoritos.value.find(num=>num===counter.value);
    console.log(numSearch);
    //Aplico un operado ternario
    if(numSearch===0) return true;
    return numSearch ? true:false; 
  })
</script>
<template>
  <Lf></Lf>
  <headerp></headerp>
  <header></header>
  <body>
    <div id="app">
      <Navar></Navar>
      <headert></headert>
      <Login></Login> 
      <h1>Hola vue js {{ name.toUpperCase() }}</h1>
      <!--<h2 :class="counter>0 ? 'positive':'negative'">{{ counter }}</h2>-->
      <h2 :class="classCounter">{{ counter }}</h2>
      <button v-on:click="increment">Aumentar</button>
      <button @click="decrement">Decrementar</button>
      <button @click="reset">Resetear</button>
      <button v-on:click="handleClick('1')">Activame 1</button>
      <button @click="handleClick('2')">Activame 2</button>
      <button @click="add" :disabled="bloquearBtnAdd">Agregar</button>
      <br>
      <!-- Código para el Token -->
      {{ arrayFavoritos }}
      <ul>
        <li v-for="(num, index) in arrayFavoritos" :key="index">
          {{ num }}
        </li>
      </ul>
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
      <p>Aquí va el arreglo de objetos</p>
      <ul>
        <template v-for="item in objetoFruta" :key="item.name">
          <li v-if="item.id > 0">{{ item.name }}</li>
        </template>
      </ul>
    </div>
    </body>
    <footerp></footerp>
</template>
<script>
  import Login from './components/Login.vue'
  export default{
    name:'App',
    components:{
      Login
    }
  }
</script>