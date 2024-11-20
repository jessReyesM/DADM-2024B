<script setup>
import PlanPickerItem from './PlanPickerItem.vue';
import {ref} from 'vue';
//creando un areferencia reactiva para almacenar el plan seleccionado
const selectedPlan = ref(null);
const plans= ref(['El cafetero', 'El chelero', 'El intelectual']);
const selectPlan = (name) => {
  //alamcenar el plan seleccionado
   selectedPlan.value = name;
};
</script>

<template>
    <div class="plans">
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