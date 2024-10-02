<script setup>
import { ref } from "vue";
//modelo 
const header = ref('App lista de Compras');
//items
const items = ref([
  {id:'0', label:'10 manzanas'}, 
  {id:'1', label:'1 leche'}, 
  {id:'2', label:'2 lata de atun'},
  {id:'3', label:'1 mermelada'},
 {id:'4', label:'1 cajeta'},
  {id:'5', label:'5 bolillos'}
]);
//item-Method

const saveItem = () => {
   items.value.push({id: items.value.length + 1, label: newItem.value});
   //limpia la entrada de la caja de texto o input
   newItem.value = '';
};
//formulario
const newItem = ref('');
const newItemPriority = ref('low');
const editing = ref(true);
const activateEdition = (activate) =>{ 
    editing.value = activate;
};
</script>

<template>
  <div class="header">
<h1>
    <i class="material-icons shopping-cart-icon">local_mall</i>
    {{ header }}
  </h1>
  <button v-if="editing" class="btn" @click="activateEdition(false)">CANCELAR</button>
  <button v-else class="btn btn-primary" @click="activateEdition(true)">AGREGAR ARTICULO</button>
</div>
<!-- Un botón de tipo submit que permite al usuario enviar el formulario para agregar el nuevo ítem a la lista.-->
 <form 
    v-on:submit.prevent="saveItem()" 
    v-if="editing"
    class="add-item fomr">
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
  <p v-if="items.length === 0"> 🥀NO HAY ELEMENTOS EN TU LISTA 🥀</p>
</template>

<style scoped>
.shopping-cart-icon{
    font-size: 2rem;
}
</style>