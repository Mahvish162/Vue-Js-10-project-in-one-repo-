
<script setup>


import {ref,computed} from 'vue'

const formData=ref({
  name:'',
  email:'',
  password:''
})
const isNameValid=computed(()=>formData.value.name.trim()!== '')
const isEmailValid=computed(()=>/^[^\&@]+@[^\&@]+\.[^\&@]+$/.test(formData.value.email))
const isPasswordValid=computed(()=>formData.value.password.length >= 8)
const isFormValid=computed(()=>isNameValid.value && isEmailValid.value && isPasswordValid.value)

const submitForm=()=>{
  if(isFormValid.value){
    console.log('Form is valid and hence submitted',formData.value)
  }else{
    console.log('Form fields are invalid....')
  }
}
</script>

<template>
  <div>
    <form @submit.prevent="submitForm" class="custom-form">
      <div class="form-group">
        <label for="name">Name : </label>
        <input v-model="formData.name" type="text" id="name">
        <span v-if="!isNameValid" class="error">Name is Required</span>
      </div>

      <div class="form-group">
        <label for="email">E-mail : </label>
        <input v-model="formData.email" type="text" id="email">
        <span v-if="!isEmailValid" class="error">Please enter a valid E-mail</span>
      </div>

      <div class="form-group">
        <label for="password">Password : </label>
        <input v-model="formData.password" type="text" id="password">
        <span v-if="!isPasswordValid" class="error">password is must be at least 8 chanarcters long</span>
      </div>

      <button type="submit" :disabled="!isFormValid"  class="submit-button">Submit</button>

    </form>
  </div>
</template>

<style scoped>
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