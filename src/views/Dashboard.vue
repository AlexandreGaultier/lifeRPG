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
        <Alimentation />
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
import Alimentation from '../components/Alimentation.vue';
export default {
  components: {
    Profile,
    Skills,
    Habits,
    Addiction,
    Logs,
    Workout,
    Alimentation
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

      ],
    };
  },
};
</script>

<style>
.dashboard {
  display: flex;
  flex-wrap: wrap;
  background-color: #F2F2F2;
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

</style>