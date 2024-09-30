<script setup>
import { ref } from "vue";
//modelo 
const header = ref('App lista de Compras');
const items = ref([
  {id:'0', label:'10 manzanas'}, 
  {id:'1', label:'1 leche'}, 
  {id:'2', label:'2 lata de atun'},
  {id:'3', label:'1 mermelada'},
 {id:'4', label:'1 cajeta'},
  {id:'5', label:'5 bolillos'}
]);
const newItem = ref('');
const newItemPriority = ref('low');
</script>

<template>
<h1>
    <i class="material-icons shopping-cart-icon">local_mall</i>
    {{ header }}
  </h1>
<!-- Un botón de tipo submit que permite al usuario enviar el formulario para agregar el nuevo ítem a la lista.-->
 <form v-on:submit.prevent="items.push({ id: items.length + 1, label: newItem })" class="add-item fomr">
    <!-- entrada de texto -->
    <input
      v-model.trim="newItem"
      type="text"
      placeholder="Add Item"
    />
    <!-- Caja de seleccion de prioridad -->
    <label>
      <input type="checkbox" v-model="newItemHighPriority" />
      High Priority
    </label>
    <!-- Boton -->
    <button
      class="btn btn-primary"
    >
      Save Item
    </button>
  </form>



  <ul>
    

    <li
         v-for="(item, i) in items" :key="item.id"> {{i+1}} {{ i%2==0?'🔥':'✨'}} {{item.label}} </li>
  </ul>
</template>

<style scoped>
.shopping-cart-icon{
    font-size: 2rem;
}
</style>