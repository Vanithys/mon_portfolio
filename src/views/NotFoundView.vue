<template>
    <div class="not-found">
      <img src="@/assets/404-image.png" alt="Image 404" class="not-found-image" />
      <h1>404</h1>
      <p>Oops ! La page que vous recherchez semble avoir disparu.</p>
      <small class="redirect-message">Vous allez être redirigé vers la page d'accueil dans quelques instants.</small>
    </div>
  </template>

<script>
export default {
  name: 'NotFoundView',
  mounted() {
    setTimeout(() => {
      this.$router.push('/')
    }, 5000)
  }
}
</script>

<style scoped>
.not-found {
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: center;
  height: 100vh;
  width: 100vw;
  text-align: center;
  background-color: #333;
  color: white;
  padding-top: 50px;
}

.not-found-image {
  max-width: 80%;
  height: auto;
}

.not-found h1 {
  font-size: 6rem;
  margin: 0;
}

.not-found p {
  font-size: 1.5rem;
  margin: 0;
}

.not-found a {
  margin-top: 1rem;
  color: #2fb3ff;
  text-decoration: none;
  font-size: 1.2rem;
}

.redirect-message {
  color: #2fb3ff;
}
</style>