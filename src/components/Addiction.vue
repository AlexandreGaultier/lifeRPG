<template>
  <div class="card addictions">
    <h2>Addictions</h2>
    <div class="addiction-icons">
        <span v-for="addiction in addictions" :key="addiction" class="addiction-icon">{{ addiction }}</span>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Addiction',
  props: {
    addictions: {
      type: Array,
      required: true
    }
  }
}
</script>
<style scoped>
.addictions {
  width: 50%;
  font-size: 1.2rem;
}

.addiction-icons {
  display: flex;
  align-items: center;
  justify-content: space-evenly;
  flex-wrap: wrap;
  gap: 3rem;
  padding: 1rem 2rem;
}

.addiction-icon {
  width: 2rem;
  height: 2rem;
  text-align: center;
  font-size: 24px;
  background-color: #f0f0f0;
  border: 1px solid #c7c7c7;
  padding: 0.7rem;
  border-radius: 10%;
}

.addiction-icon:hover {
  background-color: transparent;
  cursor: pointer;
  transition: all 0.3s ease;
}
</style>
