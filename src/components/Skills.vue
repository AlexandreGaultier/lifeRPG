<template>
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
</template>

<script>
export default {
  name: 'Skills',
  props: {
    skills: {
      type: Array,
      required: true
    }
  },
  data() {
    return {
    }
  }
}
</script>

<style scoped>

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
</style>