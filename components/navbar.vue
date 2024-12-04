<template>
  <div class="layout">
    <!-- Barra de navegación -->
    <nav class="navbar">
      <h1 class="navbar-title">Universidad de Córdoba</h1>
      <ul class="navbar-links">
        <li v-for="item in menuItems" :key="item.name">
          <router-link :to="item.path" class="navbar-link">
            {{ item.name }}
          </router-link>
        </li>
      </ul>
    </nav>

    <!-- Contenedor de contenido -->
    <div class="content">
      <slot></slot>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      menuItems: [
        { name: "Principal", path: "/" },
        { name: "Programas", path: "/programas" },
        { name: "Grupos", path: "/grupos" },
        { name: "Semilleros", path: "/semilleros" },
        { name: "Integrantes", path: "/integrantes" },
        { name: "Facultades", path: "/facultades" },
        { name: "Acerca de", path: "/acerca-de" },
        { name: "Universidad", path: "/universidad" },
      ],
    };
  },
};
</script>

<style scoped>
/* Layout general */

/* Barra de navegación */
.navbar {
  background-color: #009929;
  color: white;
  padding: 15px 20px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1); /* Sombra para separación visual */
}

.navbar-title {
  font-size: 24px;
  font-weight: bold;
  margin: 0;
}

.navbar-links {
  list-style: none;
  display: flex;
  margin: 0;
  padding: 0;
}

.navbar-link {
  color: white;
  text-decoration: none;
  margin-left: 20px;
  font-size: 16px;
  transition: color 0.2s;
}

.navbar-link:hover {
  text-decoration: underline;
  color: #cce7cc; /* Tono más claro al pasar el mouse */
}

/* Contenedor principal del contenido */

</style>