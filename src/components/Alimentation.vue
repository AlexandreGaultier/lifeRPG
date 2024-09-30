<template>
  <div class="card alimentation">
    <h2>Alimentation</h2>
    <div class="calendar">
    <div class="calendar-header">
        <span>L</span><span>M</span><span>M</span><span>J</span><span>V</span><span>S</span><span>D</span>
    </div>
    <div class="calendar-body">
        <div v-for="week in 5" :key="'week-'+week" class="calendar-week">
        <div v-for="day in 7" :key="'day-'+day+'-'+week" class="calendar-day" :class="getAlimentationClass(week, day)"></div>
        </div>
    </div>
    </div>
    <div class="alimentation-legend">
    <div class="legend-bar"></div>
    <div class="legend-labels">
      <span>1500</span>
      <span>3000</span>
    </div>
  </div>
  <div class="alimentation-buttons">
      <button class="alimentation-button">Yfood + prot</button>
      <button class="alimentation-button">Yfood</button>
      <button class="alimentation-button">Shaker</button>
      <button class="alimentation-button">Mugcake</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Alimentation',
  props: {
    alimentation: {
      type: Object,
      required: true
    }
  },
  methods: {
    getAlimentationClass(week, day) {
      // Cette méthode devrait retourner la classe appropriée pour chaque jour
      // Vous devrez implémenter la logique pour déterminer la couleur en fonction des calories consommées
      // Pour l'exemple, nous allons simplement utiliser des valeurs aléatoires
      const randomValue = Math.floor(Math.random() * 5);
      return `alimentation-level-${randomValue}`;
    }
  }
}
</script>

<style scoped>
.alimentation {
  width: 50%;
  height: 100%;
}

.calendar {
  padding: 1rem;
}

.calendar-header {
  display: grid;
  grid-template-columns: repeat(7, 1fr);
  text-align: center;
  font-weight: bold;
  margin-bottom: 0.5rem;
}

.calendar-body {
  display: grid;
  gap: 0.25rem;
}

.calendar-week {
  display: grid;
  grid-template-columns: repeat(7, 1fr);
  gap: 0.25rem;
}

.calendar-day {
  aspect-ratio: 1;
  border-radius: 20%;
  background-color: #f0f0f0;
}

.alimentation-legend {
  margin-top: 1rem;
  padding: 0 1rem;
}

.legend-bar {
  height: 10px;
  background: linear-gradient(to right, #e5f5e0, #31a354);
  margin-bottom: 5px;
}

.legend-labels {
  display: flex;
  justify-content: space-between;
  font-size: 0.8rem;
}

.alimentation-level-0 { background-color: #e5f5e0; }
.alimentation-level-1 { background-color: #c7e9c0; }
.alimentation-level-2 { background-color: #a1d99b; }
.alimentation-level-3 { background-color: #74c476; }
.alimentation-level-4 { background-color: #31a354; }

.alimentation-buttons {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
  padding: 1rem;
}

.alimentation-button {
  width: 30%;
  background-color: transparent;
  border: 1px solid #31a354;
  color: #31a354;
  padding: 0.5rem 0;
  border-radius: 20px;
  font-size: 0.9rem;
  cursor: pointer;
  transition: all 0.3s ease;
}

.alimentation-button:hover {
  background-color: #31a354;
  color: white;
}
</style>

