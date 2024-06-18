<template>
  <div id="app">
    <h1>Lista dei Progetti</h1>
    <ul>
      <li v-for="project in projects" :key="project.id">{{ project.title }}</li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      projects: [],
    };
  },
  async created() {
    try {
      // Fai una chiamata API all'endpoint Laravel per ottenere i progetti
      const response = await axios.get('http://localhost:8000/api/projects');
      // Salva i dati dei progetti nella variabile `projects`
      this.projects = response.data;
      // Stampa i dati dei progetti in console per verificarli
      console.log(response.data);
    } catch (error) {
      console.error('Errore nel recupero dei progetti:', error);
    }
  },
};
</script>

<style>
/* Puoi aggiungere il tuo stile CSS qui */
</style>
