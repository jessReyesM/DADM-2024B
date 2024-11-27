<script setup>
import PlanPickerItem from './PlanPickerItem.vue';
import {ref, onMounted, onUnmounted } from 'vue';
//creando un areferencia reactiva para almacenar el plan seleccionado
const selectedPlan = ref(null);
const plans= ref(['El cafetero', 'El chelero', 'El intelectual']);
const selectPlan = (name) => {
  //alamcenar el plan seleccionado
   selectedPlan.value = name;
};

const plansWrapper = ref(null);

//intentando obtener la referencia al elemento .plans
console.log("termina de ejecutar el scrip setup");

//registrando el hook mounted
onMounted(() => {
   console.log("el componente  PlanPicker se ha montado 🎈");
   console.log(plansWrapper.value);
});

//registrando el hook mounted
onUnmounted(()=>{
  console.log("El componente PlanPicker se ha desmontado");
});
</script>

<template>
    <div ref= "plansWrapper" class="plans">
      <PlanPickerItem 
      v-for="plan in plans" 
      :key="plan" 
      :name="plan" 
      @select="selectPlan"
      :selectPlan="selectedPlan"/>
    </div>
</template>

<style scoped>

</style>