<template>
  <div class="card logs">
        <h2>Logs</h2>
        <div class="log-container">
          <div class="log" v-for="log in logs" :key="log.date">
            <span class="log-date">{{ log.date }}</span>
            <span class="log-message">{{ log.message }}</span>
          </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Logs',
  props: {
    logs: {
      type: Array,
      required: true
    }
  }
}
</script>

<style scoped>
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

