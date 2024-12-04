<template>
    <table v-if="desarrolladores.length > 0">
      <thead>
        <tr>
          <th>ID</th>
          <th>Nombre</th>
          <th>Parte</th> 
        </tr>
      </thead>
      <tbody>
        <tr v-for="desarrollador in desarrolladores" :key="desarrollador.id">
          <td>{{ desarrollador.id }}</td>
          <td>{{ desarrollador.nombre }}</td>
          <td>{{ desarrollador.parte }}</td> 
        </tr>
      </tbody>
    </table>
    <p v-else>No hay desarrolladores para mostrar.</p>
  </template>
  
  <script>
  export default {
    props: {
      desarrolladores: Array,  
    }
  };
  </script>
  
  <style scoped>
  table {
    width: 100%;
    border-collapse: collapse;
    margin-top: 2em;
  }
  
  thead {
    background-color: #388e3c; 
    color: white;
  }
  
  th, td {
    padding: 1.2em;
    text-align: left;
    border: 1px solid #ddd;
    font-size: 1.1em;
  }
  
  th {
    background-color: #388e3c; 
    color: white;
  }
  
  td {
    background-color: #ffffff;
  }
  
  tr:nth-child(even) {
    background-color: #f1f8e9; 
  }
  
  tr:hover {
    background-color: #c8e6c9; 
  }
  
  tr:nth-child(even):hover {
    background-color: #a5d6a7; 
  }
  </style>
  
