<script setup>
    import {ref,computed} from 'vue'

    const display=ref('0')

    //this fn is just for appending the content inside the content shown division....inside first condition, if value is 0 and not . then we hv to show that particular value itself but if that's not the things, then we hv to append the values which we r pressing through the buttons and for that , we have to just add those values with former values..
    
    const appendToDisplay=(value)=>{
        if(display.value === '0' && value !== '.'){
            display.value=value
        }else{
            display.value+=value
        }
    }

    // Specifies the main fn as calculation done over here, eval() is a js fn which gives the js stuufs inside itslef...abd then convert it to string so as to add more values if wanted,
    const calculate=()=>{
        try {
            display.value=eval(display.value).toString()
        } catch (error) {
            display.value='Error'
        }
    }
    //computed property for dynamic class binding : 

    const displayClass=computed(()=>{
        return display.value.length > 12 ? 'small-text':''
    })

    const clearDisplay=()=>{
        display.value='0'
    }

</script>

<template>
    <div>
        <div class="calculator">
            <input v-model="display" :class="displayClass" readonly />
            <div class="buttons">
                <button @click="appendToDisplay('7')">7</button>
                <button @click="appendToDisplay('8')">8</button>
                <button @click="appendToDisplay('9')">9</button>
                <button @click="appendToDisplay('/')">/</button>

                <button @click="appendToDisplay('4')">4</button>
                <button @click="appendToDisplay('5')">5</button>
                <button @click="appendToDisplay('6')">6</button>
                <button @click="appendToDisplay('*')">*</button>

                <button @click="appendToDisplay('1')">1</button>
                <button @click="appendToDisplay('2')">2</button>
                <button @click="appendToDisplay('3')">3</button>
                <button @click="appendToDisplay('-')"> - </button>

                <button @click="appendToDisplay('0')">0</button>
                <button @click="appendToDisplay('.')">.</button>
                <button @click="calculate()"> =</button>
                <button @click="appendToDisplay('+')">+</button>
            </div><br>
            <button @click="clearDisplay" :class="clear-button">C</button>
        </div>
    </div>
</template>

<style>
input {
  padding: 10px 20px;
  margin-bottom: 20px;
}

.calculator {   
  max-width: 300px;
  margin: 80px auto;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 5px;
  background-color: aqua;
}

.display {
  width: 100%;
  margin-bottom: 10px;
  padding: 10px;
  font-size: 18px;
  text-align: right;
}

.buttons {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 10px;
} 
  button {
      width: 100%;
      padding: 10px;
      font-size: 18px;
      border:1px solid white;
      border-radius: 5px;
    }

button:hover{
    background-color: rgb(88, 234, 227);
}

.clear-button {
  width: 100%;
  margin-top: 10px;
}

.small-text {
  font-size: 14px;
}
</style>