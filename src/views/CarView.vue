<script setup>
import { useRoute, useRouter, RouterView } from 'vue-router';
import { ref, onBeforeMount } from 'vue';
import cars from "../data.json"

const car = ref(null)
const route = useRoute();
const router = useRouter();
const { id } = route.params

onBeforeMount(() => {
    car.value = cars.find(c => c.id === parseInt(id))
})
</script>

<template>
    <div class="container">
        <div v-if="car">
            <h1 class="car-name">{{ car.make }}</h1>
            <p>&#128677;</p>
            <p>Make: {{ car.make }}</p>
            <p>Body: {{ car.body }}</p>
            <p>Price: ${{ car.price }}</p>
            <p>Year: {{ car.year }}</p>
            <RouterView />
            <button @click="() => router.back()" class="back-button">Go Back</button>
        </div>
        <div v-else>
            <h1>Car not found</h1>
        </div>
    </div>
</template>

<style scoped>
.car-name{
    color: #3E54AC;
    font-size: 36px;
    font-weight: 700;
    margin-bottom: 10px;
}
.container {
    color: #3E54AC;
    text-align: center;
}
.back-button {
    background-color: #655DBB;
    font-size: 20px;
    color: white;

    border: none;
    border-radius: 6px;
    
    box-shadow: rgba(240, 46, 170, 0.4) 5px 5px, rgba(240, 46, 170, 0.3) 10px 10px, rgba(240, 46, 170, 0.2) 15px 15px, rgba(240, 46, 170, 0.1) 20px 20px, rgba(240, 46, 170, 0.05) 25px 25px;
    padding: 10px 20px;
    margin-top: 20px;

    cursor: pointer;
}
</style>