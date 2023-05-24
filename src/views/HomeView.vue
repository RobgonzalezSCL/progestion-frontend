<template>
  <div class="container">
    <div class="header">
    <h1>Prueba técnica</h1>
    <p>Por favor, selecciona una de las siguientes opciones:</p>
    <div class="row">
      <div class="col-2">
        <button class="btn btn-primary" @click="setDisplayToggle">Ejercicio 1</button>
      </div>
      <div class="col-2">
        <button class="btn btn-success" @click="setEditToggle">Ejercicio 2</button>
      </div>
    </div>
  </div>

  <div class="mt-2">
    <DisplayImage v-if="displayToggle"/>
    <EditRegister v-if="editToggle"/>
  </div>
  </div>

</template>

<script setup>
import { ref } from 'vue';
import DisplayImage from '@/components/ejercicio-1/DisplayImage.vue';
import EditRegister from '@/components/ejercicio-2/EditRegister.vue';

const displayToggle = ref(false);
const editToggle = ref(false);

const setDisplayToggle = () => {
  displayToggle.value = !displayToggle.value;
  editToggle.value = false;
}

const setEditToggle = () => {
  editToggle.value = !editToggle.value;
  displayToggle.value = false;
}

</script>

<style scoped>

</style>