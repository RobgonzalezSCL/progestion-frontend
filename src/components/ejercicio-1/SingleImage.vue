<template>
    <div class="card">
        <img :src="data.archivo" class="card-img mt-2" alt="Card background" />
        <div class="card-body">
            <h5 class="card-title">{{ data.nombre_archivo }}</h5>
        </div>
        <div class="card-info">
            <p><span class="text">Nombre de la foto:</span> {{ data.nombre }}</p>
            <p><span class="text">Tipo de formato:</span> {{ data.formato }}</p>
        </div>
    </div>
</template>

<script setup>
import { defineProps } from 'vue';

const props = defineProps({
    data: {
        type: Object,
        required: true
    }
})

const expanded = false;
const cambiarExpanded = () => {
    expanded = !expanded;
}

</script>

<style scoped>
.card {
    width: 300px;
    position: relative;
    margin-top: 2em;
    margin-left: 1em;
}

.card-title{
    font-weight: bold;
    font-size: 1.5em;
}
.card-img {
    width: 100%;
}

.card-info {
    bottom: 0;
    left: 0;
    width: 100%;
    background-color: rgba(28, 14, 118, 0.7);
    color: #fff;
    padding: 10px;
}

.text {
    font-weight: bold;
}
</style>