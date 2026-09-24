<script setup>
import { ref, computed } from 'vue'

const ds = ref('')
const tp = ref('')
const ex = ref('')

const moyenne = computed(() => {
  const vDs = parseFloat(ds.value) || 0
  const vTp = parseFloat(tp.value) || 0
  const vEx = parseFloat(ex.value) || 0
  return ((vDs + vTp + vEx) / 3).toFixed(2)
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
  <div class="exercice-card">
    <h2>Exercice : Calcul de Moyenne (DS + TP + EX)</h2>
    <div class="form-group">
      <label>Note DS :</label>
      <input type="number" v-model="ds" placeholder="Ex: 14" />
    </div>
    <div class="form-group">
      <label>Note TP :</label>
      <input type="number" v-model="tp" placeholder="Ex: 15" />
    </div>
    <div class="form-group">
      <label>Note EX :</label>
      <input type="number" v-model="ex" placeholder="Ex: 13" />
    </div>
    <div class="resultat" v-if="ds !== '' && tp !== '' && ex !== ''">
      <p><strong>Moyenne :</strong> {{ moyenne }} / 20</p>
      <p><strong>Mention :</strong> <span class="badge">{{ mention }}</span></p>
    </div>
  </div>
</template>

<style scoped>
.exercice-card {
  background: #f9f9f9;
  padding: 20px;
  border-radius: 8px;
  border: 1px solid #ddd;
  max-width: 400px;
  margin: 0 auto;
}
.form-group {
  margin-bottom: 15px;
  display: flex;
  justify-content: space-between;
}
input {
  padding: 5px;
  width: 150px;
}
.resultat {
  margin-top: 20px;
  padding: 10px;
  background: #e2f0d9;
  border-radius: 5px;
}
.badge {
  color: #2e7d32;
  font-weight: bold;
}
</style>