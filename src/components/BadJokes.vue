<script setup>

import axios from 'axios';
import { onMounted, ref } from 'vue';

const joke = ref()

onMounted(()=>fetchJoks())

const fetchJoks = async () => {
    try{
        const response = await axios.get("https://icanhazdadjoke.com/", {
      headers: { Accept: "application/json" },
    });


    joke.value=response.data.joke
    

        
    } catch (error) {
        console.error("Error fetching bad joke" ,error)
    }
}



</script>






<template>
    <div class="dad-jokes-container">
        <h2 class="dad-jokes-title">Dad Jokes</h2>

        <button  @click="fetchJoks" class="get-joke-button">Get Dad Joke</button>

        <div  class="dad-joke">
{{ joke }}
    </div>


</div>




</template>



<style  scoped>
.dad-jokes-container {
  max-width: 600px;
  margin: 50px auto;
}

.dad-jokes-title {
  font-size: 24px;
  color: #333;
  margin-bottom: 20px;
}

.get-joke-button {
  padding: 10px 15px;
  font-size: 16px;
  background-color: #4caf50;
  color: #fff;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

.get-joke-button:hover {
  background-color: #45a049;
}

.dad-joke {
  border: 1px solid #ddd;
  border-radius: 4px;
  padding: 15px;
  margin-top: 20px;
  background-color: #f9f9f9;
  color: #333;
}

</style>