<template>
    <div class="page-container">
      <Navbar />
      <div class="main-content">
        <h1 class="title">Programas Académicos</h1>
        <p class="intro-text">
          A continuación, podrás explorar los programas académicos, junto con su
          lista de semilleros e información relacionada.
        </p>
  
        <Accordion v-if="programas.length > 0">
          <AccordionTab
            v-for="programa in programas"
            :key="programa.id"
            :header="programa.programa"
            class="tab-green"
          >
            <p><strong>Facultad:</strong> {{ programa.facultad }}</p>
            <p><strong>Proyectos:</strong> {{ programa.proyectos }}</p>
            <Accordion>
              <AccordionTab header="Semilleros" class="semilleros-tab">
                <ul>
                  <li v-for="(semillero, index) in programa.semilleros" :key="index">
                    {{ semillero }}
                  </li>
                </ul>
              </AccordionTab>
            </Accordion>
          </AccordionTab>
        </Accordion>
        <p v-else>No se encontraron programas.</p>
      </div>
    </div>
  </template>
  
  <script>
  import Accordion from "primevue/accordion";
  import AccordionTab from "primevue/accordiontab";
  import Navbar from "@/components/Navbar.vue";
  
  export default {
    components: {
      Accordion,
      AccordionTab,
      Navbar
    },
    data() {
      return {
        programas: [],
      };
    },
    async mounted() {
      try {
        const response = await fetch("http://localhost:3001/programas");
        if (!response.ok) {
          throw new Error(`Error HTTP: ${response.status}`);
        }
        const data = await response.json();
        this.programas = data;
      } catch (error) {
        console.error("Error al obtener los datos:", error);
      }
    },
  };
  </script>
  
  <style scoped>
  .page-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: left;
    min-height: 100vh;
    background: linear-gradient(135deg, #e8f5e9, #f1f8e9);
    padding: 40px;
  }
  
  .main-content {
    text-align: left;
    max-width: 900px;
    width: 100%;
    background-color: white;
    padding: 40px;
    border-radius: 15px;
    box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
  }
  
  .title {
    font-size: 36px;
    font-weight: 600;
    color: #388e3c;
    margin-bottom: 20px;
    text-transform: uppercase;
  }
  
  .intro-text {
    font-size: 18px;
    color: #555;
    margin-bottom: 20px;
    font-style: italic;
    line-height: 1.8;
  }
  
  .tab-green {
    background-color: #009929;
    color: #fff;
    padding: 15px;
    border-radius: 8px;
  }
  
  ul {
    padding-left: 20px;
  }
  
  li {
    margin: 5px 0;
  }
  
  .semilleros-tab {
    background-color: #f1f8e9;
    padding: 15px;
    border-left: 4px solid #388e3c;
  }
  </style>