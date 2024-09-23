

<script setup>
import { ref } from 'vue';


const quotes = ref([
  {
    text: "The only way to do great work is to love what you do.",
    author: "Steve Jobs",
  },
  {
    text: "Believe you can and you're halfway there.",
    author: "Theodore Roosevelt",
  },
  {
    text: "Life is what happens when you're busy making other plans.",
    author: "John Lennon",
  },
  {
    text: "Do not despair of improving yourself.",
    author: "mahmoud Ramadn",
  },
]  
);




console.log(quotes.value[0]);
 const currentQutes=ref(quotes.value[0])


const gentRanomd = () => {

    const renmdo = Math.floor(Math.random() * quotes.value.length);


    currentQutes.value=quotes.value[renmdo]

}

</script>

<template>
  <div class="quote-generator">
    <h4 class="pp-title">Random quote  Gentreator</h4>

    <div class="quote-container ">
<p>{{ currentQutes.text }}</p>


<cite>{{ currentQutes.author }}</cite>
    </div>
    <button @click="gentRanomd" class="quote-button">GetRandmo</button>

  </div>


</template>


<style scoped>
.quote-generator {
  max-width: 400px;
  margin: 50px auto;
  padding: 20px;
  text-align: center;
  border: 1px solid #ccc;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.app-title {
  font-size: 24px;
  margin-bottom: 20px;
  color: #333;
}

.quote-container {
  background-color: #f9f9f9;
  padding: 20px;
  border-radius: 8px;
  border: 1px solid #ddd;
  margin-bottom: 20px;
}

p {
  font-size: 18px;
  margin-bottom: 10px;
}

cite {
  font-style: normal;
  color: #777;
}

.quote-button {
  padding: 10px 20px;
  font-size: 16px;
  background-color: #3498db;
  color: #fff;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

.quote-button:hover {
  background-color: #2980b9;
}
</style>