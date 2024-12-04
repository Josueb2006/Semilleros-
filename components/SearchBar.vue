<template>
    <div class="search-bar">
      <input
        :value="searchTerm"
        @input="updateSearchTerm"
        type="text"
        placeholder="🔍 Buscar grupo de investigación..."
        class="search-input"
      />
    </div>
  </template>
  
  <script setup>
  import { defineProps, defineEmits } from 'vue'
  
 
  const props = defineProps({
    searchTerm: {
      type: String,
      default: ''
    }
  })
  
  
  const emit = defineEmits(['update:searchTerm'])
  
  const updateSearchTerm = (event) => {
    
    emit('update:searchTerm', event.target.value)
  }
  </script>
  
  <style scoped>
  .search-bar {
    display: flex;
    justify-content: center;
    margin-bottom: 20px;
  }
  
  .search-input {
    width: 90%;
    max-width: 600px;
    padding: 12px 16px;
    font-size: 16px;
    border: 2px solid #4caf50;
    border-radius: 25px;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    font-family: 'Poppins', sans-serif;
    outline: none;
    transition: all 0.3s ease;
  }
  
  .search-input:focus {
    border-color: #2e7d32;
    box-shadow: 0 4px 8px rgba(46, 125, 50, 0.2);
  }
  </style>
  
