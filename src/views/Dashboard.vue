<template>
  <div class="dashboard">
    <div class="column left-column">
      <Profile />
      
      <div class="card skills">
        <h2>Skills</h2>
          <div v-for="skill in skills" :key="skill.name">
            <div :class="`skill-${skill.name}`">
              <div style="display: flex; justify-content: space-between;">
                <span class="skill-name">{{ skill.name }}</span>
                <span class="skill-level">lvl.{{ skill.level }}</span>
              </div>
              <div style="display: flex; justify-content: end;">
                <span class="skill-progress">{{ skill.progress }}/500</span>
              </div>
              <div class="skill-progress-bar" :style="{ width: skill.progress / skill.progressReach * 100 + '%' }"></div>
            </div>
          </div>
      </div>
    </div>

    <div class="column center-column">
      <div class="row">
        <div class="card habits">
          <h2>Habits</h2>
          <div class="habit-icons">
            <span v-for="habit in skills" :key="habit" :class="`habit-icon habit-${habit.name}`">{{ habit.icon }}</span>
          </div>
        </div>
        
        <div class="card addictions">
          <h2>Addictions</h2>
          <div class="addiction-icons">
            <span v-for="addiction in addictions" :key="addiction" class="addiction-icon">{{ addiction }}</span>
          </div>
        </div>
      </div>

      <div class="row">

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
      <div class="card logs">
        <h2>Logs</h2>
        <div class="log-container">
          <div class="log" v-for="log in logs" :key="log.date">
            <span class="log-date">{{ log.date }}</span>
            <span class="log-message">{{ log.message }}</span>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Profile from '../components/Profile.vue';
export default {
  components: {
    Profile
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
    getDayClass(week, day) {
      // Cette méthode devrait retourner la classe appropriée pour chaque jour
      // Vous devrez implémenter la logique pour déterminer si un jour est une séance 1, séance 2, ou vide
      // Pour l'exemple, nous allons simplement alterner entre séance 1 et séance 2
      const dayNumber = (week - 1) * 7 + day;
      if (dayNumber % 2 === 0) return 'seance-1';
      if (dayNumber % 3 === 0) return 'seance-2';
      return '';
    },
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

.skills {
  display: flex;
  flex-direction: column;
  font-size: 1.2rem;
  height: max-content;
}

.skill-Drawing {
  background: linear-gradient(to bottom, rgb(39, 125, 161, 0.4), rgb(39, 125, 161, 0.0));
  border-top: 2px solid #277DA1;
  padding: 0.5rem;
}
.skill-Code {
  background: linear-gradient(to bottom, rgb(42, 157, 143, 0.4), rgb(42, 157, 143, 0.0));
  border-top: 2px solid #2A9D8F;
  padding: 0.5rem;
}
.skill-Guitare {
  background: linear-gradient(to bottom, rgb(233, 196, 106, 0.6), rgb(233, 196, 106, 0.0));
  border-top: 2px solid #E9C46A;
  padding: 0.5rem;
}
.skill-Design {
  background: linear-gradient(to bottom, rgb(244, 162, 97, 0.6), rgb(244, 162, 97, 0.0));
  border-top: 2px solid #F4A261;
  padding: 0.5rem;
}
.skill-Writing {
  background: linear-gradient(to bottom, rgb(231, 111, 81, 0.6), rgb(231, 111, 81, 0.0));
  border-top: 2px solid #E76F51;
  padding: 0.5rem;
}
.skill-Video-Editing {
  background: linear-gradient(to bottom, rgb(67, 170, 139, 0.6), rgb(67, 170, 139, 0.0));
  border-top: 2px solid #43AA8B;
  padding: 0.5rem;
}
.skill-Reading {
  background: linear-gradient(to bottom, rgb(87, 117, 144, 0.6), rgb(87, 117, 144, 0.0));
  border-top: 2px solid #577590;
  padding: 0.5rem;
}
.skill-Running {
  background: linear-gradient(to bottom, rgb(28, 204, 5, 0.6), rgb(28, 204, 5, 0.0));
  border-top: 2px solid #1ccc05;
  padding: 0.5rem;
}

.skill-progress {
  color: #1f1f1f;
  font-size: 0.9rem;
}

.skill-progress-bar {
  height: 0.5rem;
  background-color: #383838;
  box-shadow: 0 0 0.5rem rgba(255, 255, 255, 0.4);
  border-radius: 0.5rem;
}

.addictions {
  width: 50%;
  font-size: 1.2rem;
}

.habits {
  width: 50%;
  font-size: 1.2rem;
}

.habit-icons, .addiction-icons {
  display: flex;
  align-items: center;
  justify-content: space-evenly;
  flex-wrap: wrap;
  gap: 3rem;
  padding: 1rem 2rem;
}

.habit-icon, .addiction-icon {
  width: 2rem;
  height: 2rem;
  text-align: center;
  font-size: 24px;
  background-color: #f0f0f0;
  border: 1px solid #c7c7c7;
  padding: 0.7rem;
  border-radius: 10%;
}
.habit-icon:hover, .addiction-icon:hover {
  background-color: transparent;
  cursor: pointer;
  transition: all 0.3s ease;
}

.habit-Drawing {
  background-color: rgb(39, 125, 161, 0.4);
  border: 1px solid #277DA1;
}
.habit-Code {
  background-color: rgb(42, 157, 143, 0.4);
  border: 1px solid #2A9D8F;
}
.habit-Guitare {
  background-color: rgb(233, 196, 106, 0.4);
  border: 1px solid #E9C46A;
}
.habit-Reading {
  background-color: rgb(87, 117, 144, 0.4);
  border: 1px solid #577590;
}
.habit-Design {
  background-color: rgb(244, 162, 97, 0.4);
  border: 1px solid #F4A261;
}
.habit-Writing {
  background-color: rgb(231, 111, 81, 0.4);
  border: 1px solid #E76F51;
}
.habit-Video-Editing {
  background-color: rgb(67, 170, 139, 0.4);
  border: 1px solid #43AA8B;
}
.habit-Running {
  background-color: rgba(28, 204, 5, 0.4);
  border: 1px solid #1ccc05;
}

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


.alimentation {
  width: 50%;
  height: 100%;
}

.alimentation .calendar-day {
  border-radius: 20%;
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

.logs {
  height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: start;
  gap: 1rem;
}

.log-container {
  height: 95vh;
  overflow-y: scroll;
  scrollbar-width: thin;
  scrollbar-color: #31a354 rgba(0, 0, 0, 0);
}

.log {
  padding: 0.5rem 1rem;
  border-bottom: 1px solid #ccc;
}

.log-date {
  font-weight: bold;
}

.log-message {
  display: block;
  color: #666;
}
</style>