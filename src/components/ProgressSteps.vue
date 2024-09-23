<script setup>
import {ref} from 'vue';

const steps = ref(['step 1', 'Step 2', 'Step 3'])


const currenStep = ref(0);


const nextStep = () => {
    if (currenStep.value  < steps.value.length -1 ) {
        currenStep.value++
    }
}


const prevStep = () => {
    if (currenStep.value > 0) {
        currenStep.value--
    }
}



</script>

<template>
   <div class="progress-container">
    <div class="progress-bar">
        <div v-for="(step,index) in steps" :key="index" 
        :class="{'step-active':index===currenStep}">
{{ step }}
        </div>
    </div>
    <div class="controls">
    <button @click="prevStep"  :disabled="currenStep==0"   class="btn">Previous</button>
      <button @click="nextStep" :disabled="currenStep==2" class="btn">
        Next
      </button>
    </div>
   </div>
</template>



<style  scoped>
.progress-container {
  max-width: 400px;
  margin: 50px auto;
}

.progress-bar {
  display: flex;
  background-color: #eee;
  border-radius: 8px;
  overflow: hidden;
}

.progress-bar div {
  flex: 1;
  text-align: center;
  padding: 15px;
  color: #fff;
  position: relative;
  z-index: 1;
}

.progress-bar div:not(:last-child) {
  border-right: 2px solid #fff;
}

.step-active {
  background-color: #af514c; /* Green for active step */
}

.controls {
  margin-top: 20px;
  text-align: center;
}

.btn {
  padding: 10px 20px;
  font-size: 16px;
  cursor: pointer;
  background-color: #673ab7; /* Purple for button */
  color: #fff;
  border: none;
  border-radius: 5px;
  margin: 0 5px;
}

.btn:disabled {
  background-color: #ccc;
  cursor: not-allowed;
}

</style>