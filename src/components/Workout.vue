<template>
  <div class="card workout">
          <h2 class="workout-title">Workout</h2>
          <h3 class="workout-month">September</h3>
          <p class="workout-streak">total streak 🔥 12</p>
          <div class="calendar">
            <div class="calendar-header">
              <span>L</span><span>M</span><span>M</span><span>J</span><span>V</span><span>S</span><span>D</span>
            </div>
            <div class="calendar-body">
              <div v-for="week in 5" :key="'week-'+week" class="calendar-week">
                <div v-for="day in 7" :key="'day-'+day+'-'+week" class="calendar-day" :class="getDayClass(week, day)"></div>
              </div>
            </div>
            <div class="calendar-legend">
              <div class="legend-item"><span class="legend-color seance-1"></span> Séance 1</div>
              <div class="legend-item"><span class="legend-color seance-2"></span> Séance 2</div>
            </div>
          </div>
          <h3>Exercices</h3>
          <div class="exercise-chips">
            <div class="chip séance-1 ">Biceps Curl</div>
            <div class="chip séance-1">SkullCrushers</div>
      <div class="chip séance-1">Squat</div>
      <div class="chip séance-2">Développé militaire</div>
      <div class="chip séance-2">Développé couché</div>
      <div class="chip séance-2">Rowing</div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Workout',
  methods: {
    getDayClass(week, day) {
      // Cette méthode devrait retourner la classe appropriée pour chaque jour
      // Vous devrez implémenter la logique pour déterminer si un jour est une séance 1, séance 2, ou vide
      // Pour l'exemple, nous allons simplement alterner entre séance 1 et séance 2
      const dayNumber = (week - 1) * 7 + day;
      if (dayNumber % 2 === 0) return 'seance-1';
      if (dayNumber % 3 === 0) return 'seance-2';
      return '';
    },
//   props: {
//     workout: {
//       type: Object,
//       required: true
//     }
  }
}
</script>
<style scoped>
.workout {
  width: 50%;
}

.workout-month {
  margin: 0;
  padding: 0 1rem;
}

.workout-streak {
  margin: 0;
  padding: 0 1rem;
  font-size: 0.8rem;
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

.seance-1 {
  background-color: #a8dadc;
}

.seance-2 {
  background-color: #457b9d;
}

.calendar-legend {
  display: flex;
  justify-content: center;
  margin-top: 0.5rem;
}

.legend-item {
  display: flex;
  align-items: center;
  margin: 0 0.5rem;
}

.legend-color {
  width: 1rem;
  height: 1rem;
  border-radius: 50%;
  margin-right: 0.25rem;
}

.exercise-chips {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  align-items: center;
  padding: 1rem;
  gap: 1rem;
}

.chip {
  width: 30%;
  text-align: center;
  background-color: #f0f0f0;
  padding: 0.3rem 0;
  border-radius: 20px;
  font-size: 14px;
  cursor: pointer;
  transition: all 0.3s ease;
}

.chip.séance-1 {
  color: #a8dadc;
  background-color: #fff;
  border: 2px solid #a8dadc;
}
.chip.séance-1:hover {
  color: #fff;
  background-color: #a8dadc;
  border: 2px solid #a8dadc;
}

.chip.séance-2 {
  color: #457b9d;
  background-color: #fff;
  border: 2px solid #457b9d;
}
.chip.séance-2:hover {
  color: #fff;
  background-color: #457b9d;
  border: 2px solid #457b9d;
}
</style>
