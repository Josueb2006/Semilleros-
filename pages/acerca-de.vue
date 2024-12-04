<template>
  <Navbar />
  <section class="container">
    <h1>Acerca de Nosotros</h1>
    <p class="subtitle">Este es el apartado de los trabajadores que hacen posible este proyecto.</p>

    
    <p v-if="loading" class="loading">Cargando desarrolladores...</p>
    
    <p v-if="error" class="error">{{ error }}</p>

    
    <developer-table v-if="!loading && !error" :desarrolladores="desarrolladores" />
  </section>
</template>

<script>
import DeveloperTable from '@/components/DeveloperTable.vue';

export default {
  components: {
    DeveloperTable,  
  },
  data() {
    return {
      desarrolladores: [], 
      loading: true,         
      error: null,           
    };
  },
  created() {
    this.obtenerDesarrolladores(); 
  },
  methods: {
    async obtenerDesarrolladores() {
      try {
        const respuesta = await fetch("http://localhost:3001/desarrolladores");
        if (!respuesta.ok) {
          throw new Error("No se pudo conectar con el servidor");
        }
        const data = await respuesta.json();

        
        console.log("Datos recibidos:", data);

        
        this.desarrolladores = data[0]?.desarrolladores || [];
      } catch (err) {
        this.error = `Error al cargar los desarrolladores: ${err.message}`;
        console.error(err);
      } finally {
        this.loading = false;  
      }
    }
  }
};
</script>

<style scoped>

.container {
  font-family: 'Arial', sans-serif;
  background-color: #f4f9f4;
  padding: 2rem;
  border-radius: 10px;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
  max-width: 900px;
  margin: 0 auto;
}

h1 {
  font-size: 2.5em;
  color: #2e7d32; 
  margin-bottom: 0.5em;
  text-align: center;
  font-weight: bold;
}

.subtitle {
  font-size: 1.2em;
  color: #388e3c; 
  text-align: center;
  margin-bottom: 2em;
}

.loading {
  color: #81c784; 
  text-align: center;
}

.error {
  color: #d32f2f; 
  font-weight: bold;
  text-align: center;
}
</style>
