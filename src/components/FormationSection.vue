<template>
    <section class="image-section">
      <h2 class="image-section-title">FORMATION</h2>
      <section class="image-container">
        <article class="image-card" @click="openModal(project1Images)">
          <img class="rounded-image" src="@/assets/image1_1.jpg" alt="Mon CV en ligne">
          <p class="image-text">
            Le projet consiste à créer un CV en ligne basique, mais efficace, qui présentera mes compétences et mon parcours professionnel de manière claire et concise. 
            Le design est responsive, garantissant une consultation aisée sur tous les appareils. Les sections incluent une présentation personnelle, mes compétences clés et mon expérience professionnelle. 
            Ce CV en ligne vise à offrir une visibilité optimale aux recruteurs tout en facilitant l'accès à mes informations professionnelles.
          </p>
        </article>
        <div class="vertical-separator"></div>
        <article class="image-card" @click="openModal(project2Images)">
          <img class="rounded-image" src="@/assets/image2_1.jpg" alt="Dynamiser un espace commentaire">
          <p class="image-text">
            Le projet consiste à créer un espace commentaire dynamique, permettant aux utilisateurs de laisser des avis et des retours en temps réel. 
            Le design est épuré et intuitif, garantissant une expérience utilisateur fluide. 
            Grâce à une mise à jour en temps réel, les commentaires s'affichent instantanément sans recharger la page, favorisant l'interaction entre les utilisateurs et enrichissant ainsi la communauté.
          </p>
        </article>
        <div class="vertical-separator"></div>
        <article class="image-card" @click="openModal(project3Images)">
          <img class="rounded-image" src="@/assets/image3_1.jpg" alt="Cahier des charges">
          <p class="image-text">
            L'objectif du projet est de concevoir un cahier des charges pour une entreprise hypothétique. 
            Ce document définit les besoins pour un site web moderne et responsive, visant à mettre en avant les produits et à offrir une expérience utilisateur fluide. 
            Le projet est réalisé en plusieurs phases avec des délais de validation, tout en respectant les contraintes budgétaires et techniques.
          </p>
        </article>
      </section>
  
      <Modal :isVisible="isModalVisible" :imageSrc="currentProjectImages" @close="closeModal"/>
    </section>
  </template>
  
  <script>
  import Modal from './Modal.vue';
  import image1 from '@/assets/image1_1.jpg';
  import image1_1 from '@/assets/image1_2.jpg';
  import image2 from '@/assets/image2_1.jpg';
  import image2_1 from '@/assets/image2_2.jpg';
  import image2_2 from '@/assets/image2_3.jpg';
  import image3 from '@/assets/image3_1.jpg';
  
  export default {
    name: 'FormationSection',
    components: {
      Modal,
    },
    data() {
    return {
      isModalVisible: false,
      currentProjectImages: [],
      project1Images: [
        { src: image1, date: 'Créer le 16 Septembre 2024', link: 'https://github.com/Vanithys/Mon_CV' },
        { src: image1_1, title: 'Aperçu du projet', description: 'Dans le cadre de ce devoir pratique de ma formation, le projet a été réalisé à l\'aide des langages HTML et CSS, afin d\'évaluer mes aptitudes dans le domaine de la création de pages web, en respectant les recommandations du W3C.', link: 'https://github.com/Vanithys/Mon_CV' }
      ],
      project2Images: [
        { src: image2, date: 'Créer le 15 Octobre 2024', link: 'https://github.com/Vanithys/commentaires' },
        { src: image2_1, title: 'Système de commentaires en temps réel', description: 'Dans le cadre de ce devoir pratique de ma formation, le projet a été réalisé afin d\'évaluer mes aptitudes pour dynamiser un espace commentaire en temps réel à l\'aide de Javascript.', link: 'https://github.com/Vanithys/commentaires' },
        { src: image2_2, title: 'Système de commentaires en temps réel', description: 'Lorsque l\'utilisateur omet de remplir correctement les divers champs requis dans le formulaire de rédaction, il reçoit une notification l\'avertissant que ces informations doivent être fournies.', link: 'https://github.com/Vanithys/commentaires' }
      ],
      project3Images: [
        { src: image3, date: 'En attente de création', link: 'https://github.com/Vanithys' }
      ],
    };
  },
    methods: {
      openModal(projectImages) {
        this.currentProjectImages = projectImages;
        this.isModalVisible = true;
      },
      closeModal() {
        this.isModalVisible = false;
      },
    },
  };
  </script>
  
  <style>
  .image-section {
    background-color: #333;
    padding: 70px;
    border-radius: 12px;
    max-width: 1200px;
    margin: 60px auto;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  }
  
  .image-section-title {
    text-align: center;
    font-size: 2em;
    margin-bottom: 20px;
    color: #ffffff;
  }
  
  .image-container {
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
  }
  
  .image-card {
  text-align: center;
  flex: 1 1 30%;
  margin: 10px;
  max-width: 300px;
  display: flex;
  flex-direction: column;
  align-items: center;
  cursor: pointer;
  transition: box-shadow 0.3s ease;
  }

  .image-card:hover {
  box-shadow: 4px 4px 15px rgba(0, 0, 0, 0.5);
  }
  
  .vertical-separator {
    width: 2px;
    background-color: black;
    height: 100%;
    margin: 0 10px;
  }
  
  .rounded-image {
    width: 100%;
    border-radius: 10px;
    object-fit: cover;
    max-width: 200px;
    height: auto;
  }
  
  .image-text {
    font-size: 1em;
    color: #333;
    margin: 10px;
    text-align: center;
  }
  </style>