<script setup>


  const tempSI = defineModel({
    'tempSI', {
    temperature: Number,
    unit: String,
    default: 0
  }});

  import { ref, computed, watch } from 'vue';
  //const tempSI = ref(10);
  // watch(tempSI, (newVal, oldVal) => {
  //   console.log('Temperature changed from', oldVal, 'to', newVal);
  // }); 
  const tempCelsius = computed(() => {
    return tempSI.value - 273.15;
  });
  //fareinheit
  const tempFahrenheit = computed(() => {
    return tempCelsius.value * 9/5 + 32;
  });

</script>

<template>
  <!--input pour le choix des temp et l'affichage des autres-->
  <div>
    <input type="number" :value="tempSI" @input="tempSI.value = $event.target.value" />
    <h1>Temperature Sensor</h1>
    <p>Temperature SI: {{ temperature }}</p>
    <p>Temperature C: {{ tempCelsius }}</p>
    <p>Temperature F: {{ tempFahrenheit }}</p>
  </div>
  
</template>

<style scoped>

</style>
