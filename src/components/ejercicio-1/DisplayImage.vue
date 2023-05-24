<template>
    <div class="row justify-content-center mb-5">
        <SingleImage v-for="item in apiResponse" :data="item"/>
    </div>
</template>

<script setup>
import { ref } from 'vue';
import SingleImage from '@/components/ejercicio-1/SingleImage.vue';

const apiResponse = ref(null);

// Consulta a API
const url = 'https://test.iaudisis.com/audisis/AppNat_Biblioteca/archivos';
const params = new URLSearchParams();
params.append('usuario', '22859');
params.append('accessToken', 'c2ed575f940bea5567a5b1d7dc8bd6f407c230aeebc889ced9e2ef7b226ad1204b642668725f9565a260969a8242c8227fef98fda5ecca5a72d715d8479b56eb');
params.append('carpeta', '46');

fetch(url, {
  method: 'POST',
  headers: {
    'Content-Type': 'application/x-www-form-urlencoded; charset=UTF-8'
  },
  body: params
})
  .then(response => response.json())
  .then(data => {
    apiResponse.value = data;
  })
  .catch(error => {
    console.error('Error:', error);
  });

</script>

<style scoped>

</style>