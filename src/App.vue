<template>
  <div id="app">
    <header v-if="!isNotFoundPage">
      <HeaderSection />
    </header>

    <router-view v-if="isNotFoundPage" />

    <main v-if="!isNotFoundPage">
      <section>
        <QuoteSection />
      </section>
      <section>
        <FormationSection />
      </section>
      <section>
        <ProjectSection />
      </section>
      <section>
        <ContactSection />
      </section>
    </main>

    <footer v-if="!isNotFoundPage" class="footer">
      <aside class="footer-content">
        <small>Copyright © 2024 <span class="brand-name">Vanithys</span></small>
        
        <nav class="social-icons">
          <a href="https://www.facebook.com" target="_blank">
            <img src="@/assets/facebook.png" alt="Logo de Facebook, un carré bleu avec la lettre F en blanc à l'intérieur.">
          </a>
          <a href="https://www.instagram.com/" target="_blank">
            <img src="@/assets/instagram.png" alt="Logo d'Instagram, un carré rose en dégradé avec le logo d'un appareil photo à l'intérieur.">
          </a>
          <a href="https://www.linkedin.com/" target="_blank">
            <img src="@/assets/linkedin.png" alt="Logo de Linkedin, un carré bleu avec les lettres I et N à l'interieur.">
          </a>
          <a href="https://github.com/Vanithys" target="_blank">
            <img src="@/assets/github.png" alt="Logo de GitHub, un noir avec un chat à l'intérieur">
          </a>
      </nav>

        <small class="last-updated">Dernière mise à jour : Le 29 Octobre 2024</small>
      </aside>
    </footer>
  </div>
</template>

<script>
import { computed } from 'vue';
import { useRoute } from 'vue-router';
import HeaderSection from './components/HeaderSection.vue';
import QuoteSection from './components/QuoteSection.vue';
import FormationSection from './components/FormationSection.vue';
import ProjectSection from './components/ProjectSection.vue';
import ContactSection from './components/ContactSection.vue';

export default {
  name: 'App',
  components: {
    HeaderSection,
    QuoteSection,
    FormationSection,
    ProjectSection,
    ContactSection,
  },
  setup() {
    const route = useRoute();
    const isNotFoundPage = computed(() => route.name === 'NotFound');
    
    return {
      isNotFoundPage,
    };
  },
};
</script>

<style scoped>

html, body {
  overflow-x: hidden;
}

#app {
  overflow-y: scroll;
  padding-top: 100px;
}

html {
  scroll-behavior: smooth;
}

.footer {
  background-color: #333;
  color: #fff;
  text-align: center;
  padding: 20px 0;
  font-size: 14px;
  position: relative;
  bottom: 0;
  width: 100%;
}

.footer .brand-name {
  font-weight: bold;
  color: #2fb3ff;
}

.footer small {
  margin: 0;
}

.social-icons {
  text-align: center;
  margin-top: 10px;
}

.social-icons a {
  margin: 0 10px;
}

.social-icons img {
  width: 24px;
  height: 24px;
}

@media (min-width: 1024px) {
  section {
    padding: 40px;
  }

  .footer {
    font-size: 16px;
  }
}

@media (min-width: 768px) and (max-width: 1023px) {
  section {
    padding: 30px;
  }

  .footer {
    font-size: 15px;
  }
}

@media (max-width: 767px) {
  header {
    position: static;
    padding: 10px;
  }

  section {
    padding: 15px;
  }

  .footer {
    font-size: 13px;
  }

  .footer .brand-name {
    color: #2fb3ff;
  }
}
</style>
