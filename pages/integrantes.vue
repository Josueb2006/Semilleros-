<template>
    <div class="page-container">
      <Navbar />
      
      <div class="main-content">
        <h1 class="title">Integrantes</h1>
  
        <p class="intro-text">
          Aquí encontrarás información sobre los integrantes de los semilleros de investigación. Los integrantes se dividen en tres categorías: docentes, egresados y estudiantes. 
          Cada grupo tiene sus características y roles dentro de los semilleros. A continuación, podrás ver la lista de integrantes clasificados por tipo.
        </p>
  
        <Accordion v-if="integrantes.length > 0" :value="0">
          <AccordionTab
            v-for="integrante in integrantes"
            :key="integrante.id"
            :header="integrante.nombre"
            :class="getTabClass(integrante)"
          >
            <Accordion>
              <AccordionTab header="Docentes">
                <ul>
                  <li
                    v-for="(docente, index) in integrante.integrantes.docentes || []"
                    :key="index"
                  >
                    {{ docente.nombre }}
                  </li>
                </ul>
              </AccordionTab>
            </Accordion>
  
            <Accordion>
              <AccordionTab header="Egresados">
                <ul>
                  <li
                    v-for="(egresado, index) in integrante.integrantes.egresados || []"
                    :key="index"
                  >
                    {{ egresado.nombre }}
                  </li>
                </ul>
              </AccordionTab>
            </Accordion>
  
            <Accordion>
              <AccordionTab header="Estudiantes">
                <ul>
                  <li
                    v-for="(estudiante, index) in integrante.integrantes.estudiantes || []"
                    :key="index"
                  >
                    <strong>Nombre:</strong> {{ estudiante.nombre }}<br />
                    <strong>Identificación:</strong> {{ estudiante.identificacion }}<br />
                    <strong>Semestre:</strong> {{ estudiante.semestre }}<br />
                    <strong>Teléfono:</strong> {{ estudiante.telefono }}<br />
                    <strong>Correo:</strong> {{ estudiante.correo }}<br />
                    <strong>Vinculación:</strong> {{ estudiante.vinculacion }}<br />
                  </li>
                </ul>
              </AccordionTab>
            </Accordion>
          </AccordionTab>
        </Accordion>
  
        <p v-else>No se encontraron integrantes.</p>
      </div>
    </div>
  </template>
  
  <script>
  import Accordion from "primevue/accordion";
  import AccordionTab from "primevue/accordiontab";
  
  export default {
    components: {
      Accordion,
      AccordionTab,
    },
    data() {
      return {
        integrantes: [],
      };
    },
    methods: {
      getTabClass(integrante) {
        return "tab-green";
      },
    },
    async mounted() {
      try {
        const response = await fetch("http://localhost:3001/integrantes");
        if (!response.ok) {
          throw new Error(`Error HTTP: ${response.status}`);
        }
        const data = await response.json();
        console.log("Datos recibidos:", data);
        this.integrantes = data;
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
    justify-content: center;
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
  </style>