<template>
    <Navbar />
    <div class="grupos-container">
      <h1 class="title">Grupos de Investigación</h1>
      <p class="description">
        Encuentra información sobre los grupos de investigación y sus semilleros.
        Utiliza el buscador para filtrar los grupos que te interesan.
      </p>
  
     
      <SearchBar :searchTerm="searchTerm" @update:searchTerm="updateSearchTerm" />
  
   
      <GruposTable :filteredGrupos="filteredGrupos" />
    </div>
  </template>
  
  <script setup>
  import { ref, computed, onMounted } from 'vue'
  import SearchBar from '@/components/SearchBar.vue'
  import GruposTable from '@/components/GruposTable.vue'
  
  const expandedRows = ref({})
  const grupos = ref([])
  const searchTerm = ref('')
  
  const filteredGrupos = computed(() => {
    const term = searchTerm.value.toLowerCase()
    return grupos.value.filter(grupo =>
      grupo.nombre.toLowerCase().includes(term)
    )
  })
  
  const fetchGrupos = async () => {
    try {
      const response = await fetch('http://localhost:3001/grupos')
      const data = await response.json()
      grupos.value = data[0].grupos
    } catch (error) {
      console.error('Error al obtener los datos:', error)
    }
  }
  
  onMounted(() => {
    fetchGrupos()
  })
  
  const updateSearchTerm = (newTerm) => {
    searchTerm.value = newTerm
  }
  </script>
  
  <style scoped>
  
  .grupos-container {
    max-width: 1200px;
    margin: 40px auto;
    padding: 40px;
    background: linear-gradient(135deg, #e8f5e9, #f1f8e9);
    border-radius: 15px;
    box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
    font-family: 'Poppins', sans-serif;
    text-align: center;
  }
  
  .title {
    font-size: 42px;
    font-weight: 600;
    color: #388e3c;
    text-align: center;
    margin-bottom: 15px;
    text-transform: uppercase;
  }
  
  .description {
    font-size: 18px;
    color: #555;
    text-align: center;
    margin-bottom: 40px;
    font-style: italic;
    letter-spacing: 0.5px;
  }
  
  .search-bar {
    display: flex;
    justify-content: center;
    margin-bottom: 30px;
  }
  
  .search-input {
    width: 90%;
    max-width: 600px;
    padding: 15px 20px;
    font-size: 18px;
    border: 2px solid #388e3c;
    border-radius: 30px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    font-family: 'Poppins', sans-serif;
    outline: none;
    transition: all 0.3s ease;
  }
  
  .search-input:focus {
    border-color: #2e7d32;
    box-shadow: 0 4px 8px rgba(46, 125, 50, 0.2);
  }
  
 
  .table-container {
    overflow-x: auto;
    margin-top: 30px;
  }
  
  .grupos-table {
    width: 100%;
    border-collapse: collapse;
    border-radius: 12px;
    background-color: white;
    box-shadow: 0 3px 10px rgba(0, 0, 0, 0.1);
  }
  
  .grupos-table th,
  .grupos-table td {
    padding: 18px 25px;
    text-align: left;
    font-size: 18px;
    color: #333;
  }
  
  .grupos-table th {
    background-color: #388e3c;
    color: white;
    font-weight: bold;
    border-top-left-radius: 12px;
    border-top-right-radius: 12px;
  }
  
  .group-row:hover {
    background-color: #e8f5e9;
    transition: background-color 0.3s ease;
  }
  
  .actions {
    text-align: center;
  }
  
  .btn-expand {
    background-color: #388e3c;
    color: white;
    padding: 8px 16px;
    border: none;
    border-radius: 6px;
    cursor: pointer;
    font-size: 14px;
    display: flex;
    align-items: center;
    transition: background-color 0.3s ease;
  }
  
  .btn-expand:hover {
    background-color: #2e7d32;
  }
  
  .btn-text {
    margin-right: 8px;
  }
  
  .arrow-icon {
    width: 18px;
    height: 18px;
    transition: transform 0.3s ease;
  }
  
  .arrow-icon.rotate {
    transform: rotate(180deg);
  }
  
  .semilleros-row {
    background-color: #f1f8e9;
  }
  
  .semilleros-info {
    padding: 20px;
    border-left: 4px solid #388e3c;
    background-color: #f9fbe7;
  }
  
  .semilleros-info h4 {
    font-size: 20px;
    font-weight: 600;
    color: #388e3c;
    margin-bottom: 12px;
  }
  
  .semilleros-info ul {
    padding-left: 20px;
    list-style-type: disc;
  }
  
  .semilleros-info li {
    color: #333;
    font-size: 16px;
    margin-bottom: 8px;
  }
  
  .no-semilleros {
    color: #999;
    font-style: italic;
  }
  </style>
  
