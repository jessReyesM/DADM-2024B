<template>
    <div @click="selectPlan" 
    class="plan"
    :class="{ selected: isSelected}">
    <div class="description">
      <span class="title">
         {{ name }}
         {{ isSelected ? '😊' : '' }}
      </span>
    </div>
  </div>
</template>

<script setup>
//importar la funcion propiedad computada
import { computed } from 'vue';
//usando un macro para definir las propiedades
//defineProps(['name']);
const props = defineProps({
  name: {
    type: String,
    required: true
  },
  selectPlan: String
});
//define event
const emit = defineEmits(['select']);


//metodo, funcion que permite cambiar el estado de la variable
//selected
const selectPlan = () => {
 
  //emitir evento que el plan a sido seleccionado
  emit('selec', props.name);
};
//creando una propiedad computada
//para saber si el plan ha sudo seleccionado
const isSelected = computed(() => {
  return props.name === props.selectPlan;
});
</script>

<style scoped>
</style>