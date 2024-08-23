<template>
  <div class="landing-page">
    <div class="video-background">
      <video autoplay loop muted playsinline>
        <source src="https://www.w3schools.com/howto/rain.mp4" type="video/mp4" />
      </video>
      <!-- Autre gif:
      <img src="https://media.giphy.com/media/xTkcEQACH24SMPxIQg/giphy.gif" alt="background-gif" />
      -->
    </div>
    <div class="content-overlay">
      <h1 class="title">Bienvenue à GestionPro</h1>
      <p class="subtitle">Gérez vos planifications de projets avec efficacité et simplicité</p>
     
      <router-link to="/projets"> <button class="btn-start">Commencer</button></router-link>
    </div>
  </div>
</template>

<script setup>

</script>

<style scoped>
.landing-page {
  position: relative;
  height: 100vh;
  overflow: hidden;
}

.video-background {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  overflow: hidden;
  z-index: -1;
}

video, img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  filter: blur(8px) brightness(0.7);
}

.content-overlay {
  position: relative;
  z-index: 1;
  color: white;
  text-align: center;
  top: 50%;
  transform: translateY(-50%);
}

.title {
  font-size: 3rem;
  margin-bottom: 1rem;
}

.subtitle {
  font-size: 1.5rem;
  margin-bottom: 2rem;
}

.btn-start {
  padding: 0.75rem 2rem;
  font-size: 1rem;
  color: white;
  background-color: #007bff;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.btn-start:hover {
  background-color: #0056b3;
}
</style>
