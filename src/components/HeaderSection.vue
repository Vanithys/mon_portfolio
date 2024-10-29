<template>
    <header class="header" id="app">
      <nav class="navigation">
        <ul>
          <li><router-link :to="{ hash: '#Presentation' }" :class="{ 'active-link': $route.hash === '#Presentation' }" @click.prevent="scrollToQuoteSection">PRÉSENTATION</router-link></li>
          <li><router-link :to="{ hash: '#Formation' }" :class="{ 'active-link': $route.hash === '#Formation' }" @click.prevent="scrollToFormation">FORMATION</router-link></li>
          <li>
            <router-link :to="{ hash: '#Accueil' }" @click.prevent="scrollToTop">
              <img
                :class="['logo', { swinging: isSwinging }]"
                src="@/assets/logo.png"
                alt="Logo en forme de triangle à l'envers, qui représente la lettre V et T qui fusionnent."
                @mouseenter="startSwing"
                @mouseleave="stopSwing"
              />
            </router-link>
          </li>
          <li><router-link :to="{ hash: '#Projets' }" :class="{ 'active-link': $route.hash === '#Projets' }" @click.prevent="scrollToProjects">MON PROJET</router-link></li>
          <li><router-link :to="{ hash: '#Contact' }" :class="{ 'active-link': $route.hash === '#Contact' }" @click.prevent="scrollToContact">CONTACT</router-link></li>
        </ul>
      </nav>
    </header>
  
    <div class="banner">
      <img src="@/assets/banner.jpg" alt="Le texte 'I am a student, full stack web development', accompagné de la lettre V dans un cercle sur un fond bleu." />
    </div>
  
    <nav class="sidebar-navigation">
      <div class="point" @click.prevent="scrollToTop"></div>
      <router-link to="#quote-section" class="point" @click.prevent="scrollToQuoteSection"></router-link>
      <router-link to="#image-section" class="point" @click.prevent="scrollToFormation"></router-link>
      <router-link to="#final-section" class="point" @click.prevent="scrollToProjects"></router-link>
      <router-link to="#contact-section" class="point" @click.prevent="scrollToContact"></router-link>
    </nav>
  </template>
  
  <script>
  import ScrollUtils from './ScrollUtils.vue';
  
  export default {
    name: 'HeaderSection',
    mixins: [ScrollUtils],
  
    data() {
      return {
        isSwinging: false,
      };
    },
    methods: {
      startSwing() {
        this.isSwinging = true;
      },
      stopSwing() {
        setTimeout(() => {
          this.isSwinging = false;
        }, 200);
      },
      scrollToTop() {
        this.scrollTo('body');
      },
      scrollToQuoteSection() {
        this.scrollTo('#quote-section');
      },
      scrollToFormation() {
        this.scrollTo('.image-section');
      },
      scrollToProjects() {
        this.scrollTo('.final-section');
      },
      scrollToContact() {
        this.scrollTo('.contact-section');
      },
    },
  };
  </script>

<style>
.header {
  background-color: #333;
  padding: 0px;
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  z-index: 1000;
}

.navigation {
  display: flex;
  justify-content: center;
}

.navigation ul {
  list-style-type: none;
  display: flex;
  padding: 0;
  margin: 0;
}

.navigation li {
  margin: 0 10px;
}

.navigation li a {
  margin-top: 25px;
  display: inline-block;
}

.navigation a {
  color: white;
  text-decoration: none;
  font-size: 18px;
  transition: color 0.3s;
}

.navigation a:hover {
  color: #2fb3ff;
}

.active-link {
  border-bottom: 2px solid #2fb3ff;
  color: #2fb3ff;
}

.logo {
  height: 70px;
  margin: 0;
  transition: transform 0.3s ease;
  cursor: pointer;
}

.logo.swinging {
  animation: swing 0.6s ease;
}

@keyframes swing {
  0% {
    transform: rotate(0deg);
  }
  25% {
    transform: rotate(-15deg);
  }
  50% {
    transform: rotate(15deg);
  }
  75% {
    transform: rotate(-10deg);
  }
  100% {
    transform: rotate(0deg);
  }
}

.banner {
  width: 100%;
  overflow: hidden;
}

.banner img {
  width: 100%;
  height: auto;
}

.sidebar-navigation {
  position: fixed;
  right: 20px;
  top: 50%;
  transform: translateY(-50%);
  display: flex;
  flex-direction: column;
}

.point {
  width: 10px;
  height: 10px;
  background-color: #ebebeb;
  border-radius: 50%;
  margin-bottom: 15px;
  cursor: pointer;
  transition: background-color 0.3s;
}

.point:hover {
  background-color: #2fb3ff;
}
</style>