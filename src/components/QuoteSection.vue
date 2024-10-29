<template>
    <article id="quote-section" class="quote-section">
      <h2 class="quote-title">- COURTE PRÉSENTATION -</h2>
      <blockquote class="quote">
        <span class="quote-mark">“</span>
        Bonjour, je me nomme Corentin, un passionné de développement âgé de 28 ans, originaire de la région de Bourgogne. Avec près de 10 ans d'expérience dans ce domaine, je suis actuellement en formation pour devenir Développeur web full stack.
        Mon ambition est de créer des applications et des solutions numériques qui combinent performance et convivialité. Je suis toujours à la recherche de nouvelles opportunités pour approfondir mes connaissances et relever de nouveaux défis.<br>
        <span class="align-right">Merci de visiter mon portfolio et de découvrir mes projets.</span>
        <span class="quote-mark">”</span>
      </blockquote>
      <img class="profile-pic" src="@/assets/profile.jpg" alt="Une photo d'un homme vêtu d'un casque de moto équipé d'une visière solaire, avec un masque décoré d'un crâne.">
    </article>
</template>

<script>
export default {
    name: 'QuoteSection',
};
</script>

<style scoped>
.quote-section {
  position: relative;
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 170px;
  background-color: #f4f4f4;
  border-radius: 12px;
  max-width: 1500px;
  margin: 10px auto;
  box-shadow: 0 8px 16px rgba(0, 0, 0, 0.1);
}

.quote-title {
  font-size: 2.5em;
  font-weight: bold;
  margin-bottom: 0px;
  color: #333;
  text-align: center;
  position: relative;
  top: -120px;
}

.quote {
  font-style: italic;
  font-size: 1.9em;
  color: #444;
  position: relative;
  margin-top: 30px;
  line-height: 1.7;
  text-align: justify;
}

.align-right {
  display: block;
  text-align: right;
  margin-top: 10px;
}

.quote-mark {
  font-size: 3em;
  color: #2fb3ff;
}

.quote-mark:first-child {
  position: absolute;
  top: -60px;
  left: -65px;
}

.quote-mark:last-child {
  position: absolute;
  bottom: -110px;
  right: -55px;
}

.profile-pic {
  width: 200px;
  height: 200px;
  border-radius: 50%;
  object-fit: cover;
  position: absolute;
  right: -90px;
  top: 50%;
  transform: translateY(-50%);
  border: 5px solid #f4f4f4;
}
</style>