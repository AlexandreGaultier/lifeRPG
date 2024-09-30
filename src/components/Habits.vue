<template>
  <div class="card habits">
    <h2>Habits</h2>
    <div class="habit-icons">
      <span v-for="habit in habits" :key="habit" :class="`habit-icon habit-${habit.name}`">{{ habit.icon }}</span>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Habits',
  props: {
    habits: {
      type: Array,
      required: true
    }

  }
}
</script>
<style scoped>
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
</style>
