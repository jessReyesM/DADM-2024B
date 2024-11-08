<template>
    <div class="plan">
    <div class="description">
      <span class="title">
         {{ name }}
      </span>
    </div>
  </div>
</template>

<script setup>
//usando un macro para definir las propiedades
//defineProps(['name']);
defineProps({
  name: {
    type: String,
    required: true
  }
});
</script>

<style scoped>
</style>