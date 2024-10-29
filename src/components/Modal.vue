<template>
    <div v-if="isVisible" class="modal-overlay" @click="handleOverlayClick">
      <div class="modal-content" @click.stop>
        <span class="close-icon" @click="closeModal">&times;</span>
        
        <span 
          class="nav-arrow left-arrow" 
          @click="prevImage" 
          v-if="currentIndex > 0"
        ></span>
        
        <div class="image-container">
          <h3>{{ currentImage.title }}</h3>
          <img :src="currentImage.src" alt="image" />
          <p>{{ currentImage.description }}</p>
          <p class="modal-date">{{ currentImage.date }}</p>
        </div>
        
        <span 
          class="nav-arrow right-arrow" 
          @click="nextImage" 
          v-if="currentIndex < imageSrc.length - 1"
        ></span>
  
        <button v-if="currentImage.link" class="modal-button" @click="redirectToLink(currentImage.link)">Voir le projet</button>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      isVisible: Boolean,
      imageSrc: Array,
    },
    data() {
      return {
        currentIndex: 0,
      };
    },
    computed: {
      currentImage() {
        return this.imageSrc[this.currentIndex];
      },
    },
    methods: {
      closeModal() {
        this.$emit('close');
        this.currentIndex = 0;
      },
      nextImage() {
        if (this.currentIndex < this.imageSrc.length - 1) {
          this.currentIndex++;
        }
      },
      prevImage() {
        if (this.currentIndex > 0) {
          this.currentIndex--;
        }
      },
      handleOverlayClick() {
        this.closeModal();
      },
      redirectToLink(link) {
        window.open(link, "_blank");
      }
    },
  };
  </script>
  
  <style>
  .modal-overlay {
    position: fixed;
    top: 0;
    left: 0;
    width: 100vw;
    height: 100vh;
    background: rgba(0, 0, 0, 0.7);
    display: flex;
    justify-content: center;
    align-items: center;
  }
  
  .modal-content {
    background-color: #333;
    padding: 20px;
    border-radius: 10px;
    text-align: center;
    max-width: 600px;
    width: 100%;
    position: relative;
  }
  
  .close-icon {
    position: absolute;
    top: -35px;
    right: -35px;
    font-size: 48px;
    font-weight: bold;
    color: #e0e0e0;
    cursor: pointer;
  }
  
  .close-icon:hover {
    color: #2fb3ff;
  }
  
  .nav-arrow {
    position: absolute;
    top: 50%;
    width: 0; 
    height: 0; 
    border-style: solid;
    cursor: pointer;
    transform: translateY(-50%);
    transition: border-color 0.3s, transform 0.3s;
    z-index: 10;
  }
  
  .left-arrow {
    left: -50px;
    border-width: 20px 30px 20px 0;
    border-color: transparent #fff transparent transparent;
  }
  
  .right-arrow {
    right: -50px;
    border-width: 20px 0 20px 30px;
    border-color: transparent transparent transparent #fff;
  }
  
  .nav-arrow:hover {
    border-color: transparent #2fb3ff transparent transparent;
    transform: translateY(-50%) scale(1.1);
  }
  
  .image-container img {
    max-width: 100%;
    border-radius: 10px;
  }
  
  .image-container h3, .image-container p {
    color: white;
  }
  
  .modal-date {
    color: white;
    margin-top: 10px;
  }
  
  .modal-button {
    background-color: #2fb3ff;
    color: white;
    border: none;
    border-radius: 5px;
    padding: 10px 20px;
    font-size: 1em;
    cursor: pointer;
    margin-top: 15px;
    transition: background-color 0.3s;
  }
  
  .modal-button:hover {
    background-color: #1a8db0;
  }
  </style>
  