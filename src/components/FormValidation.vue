<script setup>
import { computed, onMounted, ref } from 'vue';

const myRef = ref('');





const formdata = ref({
    name: '',
    email: '',
password:''
})


const isnameVaild = computed(() => formdata.value.name.trim() !== "")
const isEmailVaild = computed(() => /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(formdata.value.email))
const isPasswordVaild = computed(() => formdata.value.password.length>=8)


const isFormvalid = computed(() => isEmailVaild.value & isEmailVaild.value & isPasswordVaild.value)
console.log(isPasswordVaild.value,isEmailVaild.value,isnameVaild.value);


const FormData = () => {

    if (isFormvalid) {
        console.log("form submitted!" , formdata.value);
        
    
    } else {
    console.log('form is invaild . please check the fields');
    
   }

    
}



</script>



<template>
<div>
    <form class="custom-form" @submit.prevent="FormData">

        <div class="form-group">
            <label for="name">Name:</label>
            <input  v-model="formdata.name"  type="text"  id="name"  ref="myRef" >
            <span  v-if="!isnameVaild" class="error">Name is required</span>

        </div>
        <div class="form-group">
            <label for="Email">Email:</label>
            <input v-model="formdata.email"  type="email"  id="Email">
            <span v-if="!isEmailVaild" class="error">please enter a valid email address</span>

        </div>
        <div class="form-group">
            <label for="password">password:</label>
            <input v-model="formdata.password"  type="password"  id="password">
            <span v-if="!isPasswordVaild" class="error">password must be at least 8 characters </span>
        </div>

         <button type="submit"  :disabled="!isFormvalid" class="submit-button">
            Submit
         </button>
    </form>
</div>

    
</template>

<style  scoped>
.custom-form {
  max-width: 400px;
  margin: 0 auto;
}

.form-group {
  margin-bottom: 20px;
}

label {
  display: block;
  font-weight: bold;
  margin-bottom: 5px;
}

input {
  width: 100%;
  padding: 10px;
  font-size: 16px;
  border: 1px solid #ccc;
  border-radius: 4px;
}

.error {
  color: #e74c3c;
  font-size: 14px;
  margin-top: 5px;
}

.submit-button {
  padding: 10px 15px;
  font-size: 16px;
  background-color: #3498db;
  color: #fff;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

.submit-button:disabled {
  background-color: #bdc3c7;
  cursor: not-allowed;
}
</style>