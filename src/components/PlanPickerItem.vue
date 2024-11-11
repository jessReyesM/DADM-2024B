<template>
    <div @click="selectPlan" class="plan">
    <div class="description">
      <span class="title">
         {{ name }}
         {{ selected ? '😊' : '😒' }}
      </span>
    </div>
  </div>
</template>

<script setup>
//import ref fuction
import {ref} from 'vue';
//usando un macro para definir las propiedades
//defineProps(['name']);
const props = defineProps({
  name: {
    type: String,
    required: true
  }
});
//define event
const emit = defineEmits(['select']);

//variable que permite recordar si el plan ha sido seleccionado
const selected = ref(false);
//metodo, funcion que permite cambiar el estado de la variable
//selected
const selectPlan = () => {
  selected.value = true;
  //emitir evento que el plan a sido seleccionado
  emit('selec', props.name);
};
</script>

<style scoped>
</style>