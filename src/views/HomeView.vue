<script setup>
import carsData from "../data.json";
import { ref, watch, onMounted } from "vue";
import { useRouter, useRoute } from "vue-router";

const router = useRouter();
const route = useRoute();

const cars = ref(carsData);
const make = ref("");

onMounted(() => {
  make.value = route.query.make || "All";
})

watch(make, () => {
  if(make.value){
    if(make.value === "All"){
      cars.value = carsData;
    } else {
      cars.value = carsData.filter(car => car.make === make.value);
    }
  }
})

const handleChange = () => {
 router.push({query:{make: make.value}})
}
</script>

<template>
  <main class="container">
    <h1>Our cars</h1>
    <select @change="handleChange" v-model="make" class="select">
      <option value="All">All</option>
      <option value="Chevrolet">Chevrolet</option>
      <option value="Porsche">Porsche</option>
      <option value="Audi">Audi</option>
    </select>
    <div class="cards">
      <div v-for="car in cars" :key="car.id" class="card" @click="() => router.push(`/car/${car.id}`)">
        <h2>{{ car.make }}</h2>
        <p>${{ car.price }}</p>
      </div>
 
    </div>
  </main>
</template>

<style scoped>
h1 {
  color: #3E54AC;
  font-size: 36px;
  font-weight: 700;
  margin-bottom: 40px;
}

.select{
 border: 2px solid #BFACE2;
 border-radius: 6px;

 font-weight: 700;
 color: #3E54AC;

 margin-bottom: 40px;
 padding: 10px;

 box-shadow: rgba(0, 0, 0, 0.4) 0px 30px 90px;

 cursor: pointer;
}
.cards {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;

  gap: 20px;
}

.card {
  box-shadow: 1px 1px 10px rgba(0, 0, 0, 0.207);
  padding: 20px;
  width: 150px;

  display: flex;
  flex-direction: column;
  align-items: center;

  color: white;
  background-color: #655DBB;
  border-radius: 6px;
  cursor: pointer;
}

p {
  color: white;
  font-size: 18px;
  font-weight: 600;
}
</style>
