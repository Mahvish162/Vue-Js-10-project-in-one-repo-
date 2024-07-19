
<script setup>

import {ref} from 'vue'

const items=ref([
  {
    title:'What is HTML ?',
    content:"html is hyper text marup language.",
    open:false,
  },
  {
    title:'What is CSS ?',
    content:"CSS stands for Casscading styling sheet",
    open:false,
  },
  {
    title:'What is JS ?',
    content:"JS stands for Java script..",
    open:false,
  },
])


const toggleAccordian=(index)=>{
  items.value=items.value.map((item,i)=>({
    ...item,
    open:i=== index ? !item.open : false
  }))
}


</script>
<template>
  <div class="accordian-container">
    <div v-for="(item,index) in items" :key="index" class='accordion'>
      <div class="accordion-header" @click="toggleAccordian(index)">
        {{ item.title }}
        <span class="arrow-icon">
          {{ item.open ? "😍" : "😒" }}
        </span>      
    </div>

    <div v-show="item.open" class="accordian-content">{{ item.content }}</div>

    </div>
  </div>
</template>

<style scoped>
.accordion-container {
  max-width: 600px;
  margin: 50px auto;
}

.accordion {
  border: 1px solid #ddd;
  border-radius: 4px;
  overflow: hidden;
  margin-bottom: 10px;
}

.accordion-header {
  background-color: #3498db;
  color: #fff;
  padding: 15px;
  cursor: pointer;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.arrow-icon {
  font-size: 20px;
}

.accordion-content {
  padding: 15px;
  display: none;
  border-top: 1px solid #ddd;
  background-color: #f9f9f9;
  color: #333;
}

.accordion-content[style] {
  display: block;
}
</style>