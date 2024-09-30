<template>
  <div class="dashboard">
    <div class="column left-column">
      <Profile />
      
      <Skills :skills="skills" />
    </div>

    <div class="column center-column">
      <div class="row">
        <Habits :habits="skills" />
        
        <Addiction :addictions="addictions" />
      </div>

      <div class="row">

        <Workout />
        
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
      </div>
    </div>

    <div class="column right-column">
      <Logs :logs="logs" />
    </div>
  </div>
</template>

<script>
import Profile from '../components/Profile.vue';
import Skills from '../components/Skills.vue';
import Habits from '../components/Habits.vue';
import Addiction from '../components/Addiction.vue';
import Logs from '../components/Logs.vue';
import Workout from '../components/Workout.vue';
export default {
  components: {
    Profile,
    Skills,
    Habits,
    Addiction,
    Logs,
    Workout
  },
  name: 'Dashboard',
  data() {
    return {
      skills: [
        { name: 'Drawing', level: 3, progress: 80, progressReach: 200, color: '#277DA1', icon: '✏️' },
        { name: 'Code', level: 3, progress: 110, progressReach: 600, color: '#2A9D8F', icon: '💻' },
        { name: 'Guitare', level: 3, progress: 110, progressReach: 400, color: '#E9C46A', icon: '🎸' },
        { name: 'Reading', level: 3, progress: 60, progressReach: 120, color: '#F4A261', icon: '📚' },
        { name: 'Design', level: 3, progress: 100, progressReach: 150, color: '#E76F51', icon: '🎨' },
        { name: 'Writing', level: 3, progress: 30, progressReach: 100, color: '#577590', icon: '📝' },
        { name: 'Video-Editing', level: 3, progress: 40, progressReach: 120, color: '#43AA8B', icon: '🎞️' },
        { name: 'Running', level: 3, progress: 40, progressReach: 120, color: '#43AA8B', icon: '🏃‍♂️' },
      ],
      addictions: ['📱', '▶️', '🎮', '⏲', '', '', '', ''],
      logs: [
        { date: '12 mars 2023 10:30', message: 'You gained +5 exp in Reading.' },
        { date: '15 avril 2023 14:15', message: 'You gained +5 exp in Reading.' },
        { date: '20 mai 2023 16:00', message: 'You gained +5 exp in Reading.' },
        { date: '25 juin 2023 11:45', message: 'You gained +5 exp in Reading.' },
        { date: '30 juillet 2023 13:30', message: 'You gained +5 exp in Reading.' },
        { date: '04 août 2023 15:15', message: 'You gained +5 exp in Reading.' },
        { date: '04 août 2023 15:15', message: 'You gained +5 exp in Reading.' },
        { date: '04 août 2023 15:15', message: 'You gained +5 exp in Reading.' },
        { date: '04 août 2023 15:15', message: 'You gained +5 exp in Reading.' },
        { date: '04 août 2023 15:15', message: 'You gained +5 exp in Reading.' },
        { date: '04 août 2023 15:15', message: 'You gained +5 exp in Reading.' },
        { date: '04 août 2023 15:15', message: 'You gained +5 exp in Reading.' },
        { date: '04 août 2023 15:15', message: 'You gained +5 exp in Reading.' },
        { date: '04 août 2023 15:15', message: 'You gained +5 exp in Reading.' },
        { date: '04 août 2023 15:15', message: 'You gained +5 exp in Reading.' },

        // ... ajoutez plus de logs ici
      ],
    };
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
};
</script>

<style>
.dashboard {
  display: flex;
  flex-wrap: wrap;
  background-color: #F2F2F2; /* #5AC3A6 */
  color: #000;
  min-height: 100vh;
  padding: 20px;
  gap: 20px;
}

.row {
  display: flex;
  width: 100%;
  gap: 1.5rem;
  align-items: center;
}
.column {
  width: 100%;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  gap: 1.5rem;
}

.left-column, .right-column {
  flex: 2;
}

.center-column {
  flex: 6;
}

.card {
  background-color: white;
  border-radius: 0.5rem;
  box-shadow: 0 0 4px rgba(0, 0, 0, 0.25);
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  box-shadow: 0 0 0.5rem #00000041;
  transition: all 0.3s ease;
}
.card:hover {
  box-shadow: 0 0 0.5rem #00000085;
  transform: translateY(5px);
}

h2 {
  padding: 1rem;
  margin: 0;
  font-size: 1.5rem;
  font-weight: 400;
}

h3 {
  padding: 1rem;
  margin: 0;
  font-size: 1.2rem;
}



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