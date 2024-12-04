<template>
  <center>
    <h1>Semillero</h1>
  </center>
  <div v-for="semillero in semilleros" key="semillero.id">
      <p>{{ semillero.nombre }}</p>
    </div>
  <div>
 
    <button @click="downloadDocument('/Semillero RedLenguaje.pdf')">Descargar Semillero RedLenguaje</button>
    <br><br>
    <button @click="downloadDocument('/Semillero Bimadino.pdf')">Descargar Semillero Bimadino</button>
    <br><br>
    <button @click="downloadDocument('/Semillero EduSAEFI+.pdf')">Descargar Semillero EduSAEFI+</button>
    <br><br>
    <button @click="downloadDocument('/Semillero EdAmSis.pdf')">Descargar Semillero EdAmSis</button>
    <br><br>
    <button @click="downloadDocument('/Semillero SEDHYM.pdf')">Descargar Semmillero SEDHYM</button>
    <br><br>
    <button @click="downloadDocument('/Semillero Ataraxia.pdf')">Descargar Semillero Ataraxia</button>
    <br><br>
    <button @click="downloadDocument('/Semillero Homoludens.pdf')">Descargar Semillero  Homoludens</button>
    <br><br>
    <button @click="downloadDocument('/Semillero LEXICON.pdf')">Descargar Semillero LEXICON</button>
    <br><br>
    <button @click="downloadDocument('/Semillero DIDACIEN.pdf')">Descargar Semillero  DIDACIEN</button>
    <br><br>
    <button @click="downloadDocument('/Semillero AVI.pdf')">Descargar Semillero AVI</button>
    <br><br>
    <button @click="downloadDocument('/Semillero GPS.pdf')">Descargar Semillero GPS</button>
    <br><br>
    <button @click="downloadDocument('/Semillero Red Neuronal.pdf')">Descargar Semillero Red Neuronal</button>
    <br><br>
    <button @click="downloadDocument('/Semillero Génesis.pdf')">Descargar Semillero Génesis</button>
    <br><br>
    <button @click="downloadDocument('/Semillero LabSIE.pdf')">Descargar Semillero LabSIE</button>
    <br><br>
    <button @click="downloadDocument('/Semillero EXPRESARTE.pdf')">Descargar Semillero EXPRESARTE</button>
    <br><br>
    <button @click="downloadDocument('/Semillero REPENSARTE.pdf')">Descargar Semillero Repensarte</button>
    <br><br>
    <button @click="downloadDocument('/Semillero Sentia.pdf')">Descargar Semillero Sentia</button>
    <br><br>
    <button @click="downloadDocument('/Semillero GESTAD.pdf')">Descargar Semillero GESTAD</button>
    <br><br>
    <button @click="downloadDocument('/Semillero GEOSOCIAL.pdf')">Descargar Semillero GEOSOCIAL</button>
  </div>
</template>
<script setup>
import semilleros from '@/static/db.json'

</script>
