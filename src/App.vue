<script setup>
import { ref } from "vue";
//modelo 
const header = ref('App lista de Compras');
//items
const items = ref([
  {id:'0', label:'10 manzanas', purchased: true, priority: true}, 
  {id:'1', label:'1 leche', purchased: false, priority: false}, 
  {id:'2', label:'2 lata de atun', purchased: false, priority: true},
  {id:'3', label:'1 mermelada', purchased: true, priority: false},
 {id:'4', label:'1 cajeta', purchased: false, priority: true},
  {id:'5', label:'5 bolillos', purchased: false, priority: true}
]);
//item-Method

const saveItem = () => {
   items.value.push({id: items.value.length + 1, label: newItem.value});
   //limpia la entrada de la caja de texto o input
   newItem.value = '';
};

//metodo del hipervinculo
const hipervinculo = () => {
    return newItem.value === '' ? 'https://www.google.com' :
    'https://' + newItem.value;
}

//formulario
const newItem = ref('');
const newItemPriority = ref('low');
const editing = ref(true);
const activateEdition = (activate) =>{ 
    editing.value = activate;
// Alternando estado de compra del item
const togglePurchased = (item) => {
  item.purchased = !item.purchased;
}
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
    :disabled="newItem.length == 0"
      class="btn btn-primary"
    >
      Save Item
    </button>
  </form>

  <!--<a v-bind:href="hipervinculo()" target="_blank">
  {{ newItem == '' ? 'link' : newItem }}
</a>-->
<!--lista-->
<ul>
  <li
    v-for="item in items"
    @click="togglePurchased(item)"
    v-bind:key="item.id"
    :class="[{ strikeout: item.purchased }, { [item.priority]: item.highPriority }]"
  >
    ⚜ {{ item.label }}
  </li>
</ul>

  <p v-if="items.length === 0"> 🥀NO HAY ELEMENTOS EN TU LISTA 🥀</p>

<!--lista con arreglos
<ul>
    <li
         v-for="{label, id, purchased, priority} in items" 
         :key="id" 
         :class="[purchased ? 'strikeout': '', priority ? 'priority' : '']"> 
         {{priority ? "🎈": "🌸"}} {{label}} </li>
  </ul>
  <p v-if="items.length === 0"> 🥀NO HAY ELEMENTOS EN TU LISTA 🥀</p>-->


</template>

<style scoped>
.shopping-cart-icon{
    font-size: 2rem;
}
</style>