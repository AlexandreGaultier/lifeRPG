<template>
<div class="card profile">
    <div class="row">
      <div class="column">
        <div class="row" style="justify-content: space-between;">
          <h2 class="profile-title">William Saurin</h2>
          <span class="profile-level">Lv.12</span>
        </div>
        <p class="profile-subtitle">Subtitle to change every days</p>
      </div>
        <img class="profile-image" src="../assets/beluga.jpg" alt="Profile">
    </div>
    <div class="presentation">
      <p class="presentation-title">Présentation</p>
      <p class="presentation-content">Lorem ipsum dolor, sit amet consectetur adipisicing elit. Repudiandae magnam voluptatem illo iste asperiores !</p>
    </div>
</div>
</template>

<script>
export default {
  name: 'Profile',
  data() {
    return {
      
    }
  }
}
</script>

<style scoped>
.profile {
  height: 100%;
  display: flex;
  flex-direction: column;
  align-items: start;
  justify-content: space-between;
}

.profile h2 {
  margin: 0;
  padding: 0 1rem;
}

.profile p {
  margin: 0;
  padding: 0 1rem;
}

.profile-image {
  width: 100px;
  height: 100px;
  padding: 1rem;
  border-radius: 20%;
}

.presentation {
  padding: 1rem 0;
  text-align: justify;
}

.presentation-title {
  font-size: 1.2rem;
  font-weight: bold;
}

</style>
