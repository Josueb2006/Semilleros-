<template>
  <div>
    <Navbar />

    <div class="facultades-container">
      <h1 class="title">Facultades</h1>
      <p class="intro-text">
        Las facultades adscritas a los semilleros de investigación representan el compromiso académico y profesional de nuestras instituciones educativas. Cada facultad colabora estrechamente con sus respectivos semilleros, fomentando la investigación y el desarrollo en diversas áreas del conocimiento. Además, se presentan sus programas académicos más destacados, los grupos de trabajo que lideran iniciativas clave y los proyectos innovadores que reflejan el avance y la excelencia en sus campos específicos. Esta sinergia busca promover la formación integral, la generación de nuevo conocimiento y el impacto positivo en la sociedad.
      </p>

      <Accordion v-if="facultades.length > 0" :value="0">
        <AccordionTab
          v-for="facultad in facultades"
          :key="facultad.id"
          :header="facultad.nombre"
          class="accordion-tab"
        >
          <Accordion>
            <AccordionTab header="Semilleros">
              <ul>
                <li
                  v-for="(semillero, index) in facultad.semilleros || []"
                  :key="index"
                >
                  {{ semillero }}
                </li>
              </ul>
            </AccordionTab>
          </Accordion>

          <Accordion>
            <AccordionTab header="Programas">
              <ul>
                <li
                  v-for="(programa, index) in facultad.programas || []"
                  :key="index"
                >
                  {{ programa }}
                </li>
              </ul>
            </AccordionTab>
          </Accordion>

          <Accordion>
            <AccordionTab header="Grupos">
              <ul>
                <li
                  v-for="(grupo, index) in facultad.grupos || []"
                  :key="index"
                >
                  {{ grupo }}
                </li>
              </ul>
            </AccordionTab>
          </Accordion>

          <h3 class="projects-title">Proyectos</h3>
          <p>{{ facultad.proyectos || 'No hay proyectos disponibles.' }}</p>
        </AccordionTab>
      </Accordion>

      <p v-else class="no-data-message">No se encontraron facultades.</p>
    </div>
  </div>
</template>

<script>
import Accordion from "primevue/accordion";
import AccordionTab from "primevue/accordiontab";
import Navbar from "../components/navbar.vue";

export default {
  components: {
    Accordion,
    AccordionTab,
    Navbar,
  },
  data() {
    return {
      facultades: [],
    };
  },
  methods: {
    getTabClass(facultad) {
      return "tab-green";
    },
  },
  async mounted() {
    try {
      const response = await fetch("http://localhost:3001/facultades");
      if (!response.ok) {
        throw new Error(`Error HTTP: ${response.status}`);
      }
      const data = await response.json();
      console.log("Datos recibidos:", data);
      this.facultades = data;
    } catch (error) {
      console.error("Error al obtener los datos:", error);
    }
  },
};
</script>

<style scoped>
.facultades-container {
  max-width: 1200px;
  margin: 40px auto;
  padding: 40px;
  background: linear-gradient(135deg, #e8f5e9, #f1f8e9);
  border-radius: 15px;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
  font-family: 'Poppins', sans-serif;
  text-align: left;
}

.title {
  font-size: 42px;
  font-weight: 600;
  color: #388e3c;
  text-align: center;
  margin-bottom: 15px;
  text-transform: uppercase;
}

.intro-text {
  font-size: 18px;
  color: #555;
  text-align: left;
  margin-bottom: 40px;
  font-style: italic;
  letter-spacing: 0.5px;
}

.accordion-tab {
  margin-bottom: 15px;
}

.tab-green {
  background-color: #388e3c;
  color: white;
  padding: 15px;
  border-radius: 8px;
}

.projects-title {
  font-size: 24px;
  font-weight: bold;
  color: #2e7d32;
  margin-top: 20px;
}

.no-data-message {
  font-size: 18px;
  color: #999;
  font-style: italic;
}
</style>