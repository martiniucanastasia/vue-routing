<script setup>
import { useRouter } from 'vue-router';

const router = useRouter();
</script>

<template>
    <div class="container">
        <h1>404 - Not Found</h1>
        <button @click="() => router.back()" class="back-button">Go Back</button>
    </div>
</template>

<style scoped>
h1 {
    color: #3E54AC;
    font-size: 36px;
    font-weight: 700;
    margin-bottom: 10px;
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