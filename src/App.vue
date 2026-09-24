<script setup>
import { ref } from 'vue'
import CalculMoyenne from './components/CalculMoyenne.vue'
import Compteur from './components/Compteur.vue'
const exerciceActif = ref('moyenne')
</script>
<template>
  <main class="main-container">
    <h1>Mes Exercices Vue.js</h1>
    <nav class="menu">
      <button 
        @click="exerciceActif = 'moyenne'" 
        :class="{ active: exerciceActif === 'moyenne' }"
      >
        Exercice 1 : Calcul Moyenne
      </button>
      <button 
        @click="exerciceActif = 'compteur'" 
        :class="{ active: exerciceActif === 'compteur' }"
      >
        Exercice 2 : Compteur
      </button>
    </nav>
    <div class="content">
      <CalculMoyenne v-if="exerciceActif === 'moyenne'" />
      <Compteur v-if="exerciceActif === 'compteur'" />
    </div>
  </main>
</template>

<style>
body {
  font-family: Arial, sans-serif;
  background-color: #f4f7f6;
  margin: 0;
  padding: 20px;
}
.main-container {
  max-width: 600px;
  margin: 0 auto;
  text-align: center;
}
.menu {
  margin-bottom: 30px;
  display: flex;
  justify-content: center;
  gap: 15px;
}
.menu button {
  padding: 10px 15px;
  font-size: 16px;
  cursor: pointer;
  border: 1px solid #42b883;
  background-color: white;
  color: #42b883;
  border-radius: 5px;
  transition: 0.3s;
}
.menu button.active {
  background-color: #42b883;
  color: white;
  font-weight: bold;
}
.menu button:hover {
  background-color: #35495e;
  color: white;
  border-color: #35495e;
}
</style>