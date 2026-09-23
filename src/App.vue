<script setup>
import { ref, computed } from 'vue'

const ds = ref(0)
const tp = ref(0)
const ex = ref(0)

const moyenne = computed(() => {
  return ((Number(ds.value) + Number(tp.value) + Number(ex.value)) / 3).toFixed(2)
})

const mention = computed(() => {
  const m = parseFloat(moyenne.value)
  if (m >= 16) return 'Très Bien'
  if (m >= 14) return 'Bien'
  if (m >= 12) return 'Assez Bien'
  if (m >= 10) return 'Passable'
  return 'Insuffisant'
})
</script>

<template>
  <div class="container">
    <h1>Calcul de Moyenne</h1>

    <div class="form-group">
      <label>Note DS :</label>
      <input type="number" v-model="ds" min="0" max="20" step="0.25" />
    </div>

    <div class="form-group">
      <label>Note TP :</label>
      <input type="number" v-model="tp" min="0" max="20" step="0.25" />
    </div>

    <div class="form-group">
      <label>Note EX :</label>
      <input type="number" v-model="ex" min="0" max="20" step="0.25" />
    </div>

    <div class="result">
      <p><strong>Moyenne :</strong> {{ moyenne }} / 20</p>
      <p><strong>Mention :</strong> {{ mention }}</p>
    </div>
  </div>
</template>

<style scoped>
.container {
  max-width: 400px;
  margin: 50px auto;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 8px;
  font-family: Arial, sans-serif;
  text-align: center;
}

.form-group {
  margin-bottom: 15px;
  text-align: left;
}

.form-group label {
  display: block;
  margin-bottom: 5px;
  font-weight: bold;
}

.form-group input {
  width: 100%;
  padding: 8px;
  box-sizing: border-box;
}

.result {
  margin-top: 20px;
  padding: 15px;
  background-color: #f0f0f0;
  border-radius: 6px;
  color: #000;
}
</style>