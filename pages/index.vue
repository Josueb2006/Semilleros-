<template>
  <div class="page-container">
    <Navbar />

    <div class="main-content">
      <h2 class="title">Bienvenidos a los Semilleros de Investigación</h2>

      <div class="logo-container">
        <img src="/logo.png" alt="Logo Universidad de Córdoba" class="logo" />
      </div>

      <p class="intro-text">
        Este es el repositorio oficial para los semilleros de investigación de la Universidad de Córdoba. Actualmente, tenemos registrados 18 semilleros en nuestra base de datos.
      </p>

      <p class="info-text">
        Puedes encontrar más información sobre los semilleros, programas, grupos de investigación y proyectos destacados en las distintas secciones del sitio.
      </p>

      <div class="additional-info">
        <p>Explora las páginas para obtener más detalles sobre cada uno de los semilleros y las actividades que realizan.</p>
      </div>
    </div>
  </div>
</template>

<script>
import Navbar from "../components/navbar.vue";

export default {
  components: {
    Navbar,
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
  text-align: center;
  max-width: 800px;
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

.logo-container {
  margin: 30px 0;
}

.logo {
  max-width: 200px;
  height: auto;
  margin-bottom: 20px;
}

.intro-text {
  font-size: 18px;
  color: #555;
  margin-bottom: 20px;
  font-style: italic;
  line-height: 1.8;
}

.info-text {
  font-size: 18px;
  color: #666;
  margin-bottom: 30px;
  line-height: 1.8;
}

.additional-info {
  font-size: 16px;
  color: #333;
  padding: 20px;
  background: #f9fbe7;
  border-left: 4px solid #388e3c;
  border-radius: 8px;
}
</style>