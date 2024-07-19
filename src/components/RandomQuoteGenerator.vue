<script setup>
    import {ref,onMounted} from 'vue'
    const quotes=ref([
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
    ])

    const currentQuote=ref({text:"",author:""})
    const getRandomQuote=()=>{
        const rndmIndex=Math.floor(Math.random()*quotes.value.length)

        currentQuote.value=quotes.value[rndmIndex]
    }
    onMounted(getRandomQuote)
</script>

<template>
    <div class="quote-generator">
        <h1 class="app-title">Random code generator</h1>
        <blockquote class="quote-container">
            <p>{{ currentQuote.text }}</p>
            <cite>{{ currentQuote.author }}</cite>
        </blockquote>
        <button @click="getRandomQuote" class="quote-button">Get Random Quote</button>
    </div>
</template>

<style scoped>
.quote-generator {
  max-width: 400px;
  margin: 50px auto;
  padding: 20px;
  text-align: center;
  border: 3px solid #d10c92;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.app-title {
  font-size: 28px;
  font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
  margin-bottom: 20px;
  color: #333;
}

.quote-container {
  background-color: #e540ab;
  padding: 20px;
  border-radius: 8px;
  border: 1px solid #ddd;
  margin-bottom: 20px;
  color:white;
}
p {
  font-size: 18px;
  margin-bottom: 10px;
}

cite {
  font-style: normal;
  color:white;
}

.quote-button {
  padding: 10px 20px;
  font-size: 16px;
  background-color:#e540ab;
  color: hsl(135, 10%, 92%);
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

.quote-button:hover {    
  background-color: #4d34db;
}
.quote-container:hover{
    background-color: #4d34db;
}
</style>