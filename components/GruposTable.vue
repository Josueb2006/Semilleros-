<template>
    <div class="table-container">
      <table class="grupos-table">
        <thead>
          <tr>
            <th>ID</th>
            <th>Nombre del Grupo de Investigación</th>
            <th class="actions">Acciones</th>
          </tr>
        </thead>
        <tbody>
          <template v-for="grupo in filteredGrupos" :key="grupo.id">
          
            <tr class="group-row">
              <td>{{ grupo.id }}</td>
              <td>{{ grupo.nombre }}</td>
              <td>
                <button 
                  @click="toggleSemilleros(grupo.id)"
                  class="btn-expand"
                >
                  <span class="btn-text">Ver Semilleros</span>
                  <svg 
                    :class="['arrow-icon', expandedRows[grupo.id] ? 'rotate' : '']"
                    fill="none" 
                    stroke="currentColor" 
                    viewBox="0 0 24 24"
                  >
                    <path 
                      stroke-linecap="round" 
                      stroke-linejoin="round" 
                      stroke-width="2" 
                      d="M19 9l-7 7-7-7"
                    />
                  </svg>
                </button>
              </td>
            </tr>
           
            <tr v-if="expandedRows[grupo.id]" class="semilleros-row">
              <td colspan="3">
                <div class="semilleros-info">
                  <h4>Semilleros:</h4>
                  <div v-if="grupo.semilleros && grupo.semilleros.length > 0">
                    <ul>
                      <li 
                        v-for="semillero in grupo.semilleros" 
                        :key="semillero"
                      >
                        {{ semillero }}
                      </li>
                    </ul>
                  </div>
                  <p v-else class="no-semilleros">No hay semilleros vinculados a este grupo</p>
                </div>
              </td>
            </tr>
          </template>
        </tbody>
      </table>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue'
  
  const props = defineProps({
    filteredGrupos: {
      type: Array,
      required: true
    }
  })
  
  const expandedRows = ref({})
  
  const toggleSemilleros = (grupoId) => {
    expandedRows.value[grupoId] = !expandedRows.value[grupoId]
  }
  </script>
  
  <style scoped>
 
  .table-container {
    overflow-x: auto;
  }
  
  .grupos-table {
    width: 100%;
    border-collapse: collapse;
    border-radius: 8px;
    background-color: white;
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
  }
  
  .grupos-table th,
  .grupos-table td {
    padding: 16px 20px;
    text-align: left;
    font-size: 16px;
    color: #333;
  }
  
  .grupos-table th {
    background-color: #4caf50;
    color: white;
    font-weight: bold;
  }
  
  .group-row:hover {
    background-color: #f1fdf0;
    transition: background-color 0.3s ease;
  }
  
  .actions {
    text-align: center;
  }
  
  .btn-expand {
    background-color: #4caf50;
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
    background-color: #45a049;
  }
  
  .btn-text {
    margin-right: 8px;
  }
  
  .arrow-icon {
    width: 16px;
    height: 16px;
    transition: transform 0.3s ease;
  }
  
  .arrow-icon.rotate {
    transform: rotate(180deg);
  }
  
  .semilleros-row {
    background-color: #e6f7e6;
  }
  
  .semilleros-info {
    padding: 20px;
    border-left: 4px solid #4caf50;
  }
  
  .semilleros-info h4 {
    font-size: 18px;
    font-weight: 600;
    color: #4caf50;
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
  
