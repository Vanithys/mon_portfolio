<template>
    <section class="contact-section">
      <h2>Contactez-nous</h2>
      <form @submit.prevent="submitForm">
        <div class="form-group">
          <label for="firstName">Prénom</label>
          <input type="text" id="firstName" v-model="formData.firstName" required>
        </div>
        <div class="form-group">
          <label for="lastName">Nom</label>
          <input type="text" id="lastName" v-model="formData.lastName" required>
        </div>
        <div class="form-group">
          <label for="subject">Objet</label>
          <input type="text" id="subject" v-model="formData.subject" required>
        </div>
        <div class="form-group">
          <label for="message">Message</label>
          <textarea id="message" v-model="formData.message" required></textarea>
        </div>
        <button type="submit">Envoyer</button>
      </form>
      <div v-if="submitted" class="success-message">
        Merci ! Votre message a été envoyé.
      </div>
    </section>
  </template>
  
  <script>
  import emailjs from 'emailjs-com';
  
  export default {
    name: 'ContactSection',
    data() {
      return {
        formData: {
          firstName: '',
          lastName: '',
          subject: '',
          message: '',
        },
        submitted: false,
      };
    },
    methods: {
      async submitForm() {
        console.log("Form submitted:", this.formData);
        try {
          const response = await emailjs.send(
            import.meta.env.VITE_EMAILJS_SERVICE_ID,
            import.meta.env.VITE_EMAILJS_TEMPLATE_ID,
            {
              first_name: this.formData.firstName,
              last_name: this.formData.lastName,
              subject: this.formData.subject,
              message: this.formData.message,
            },
            import.meta.env.VITE_EMAILJS_USER_ID
          );
  
          console.log("Email sent successfully:", response);
          if (response.status === 200) {
            this.submitted = true;
            this.resetForm();
            setTimeout(() => {
              this.submitted = false;
            }, 5000);
          } else {
            console.error('Erreur lors de l\'envoi de l\'email');
          }
        } catch (error) {
          console.error('Erreur:', error);
        }
      },
      resetForm() {
        this.formData.firstName = '';
        this.formData.lastName = '';
        this.formData.subject = '';
        this.formData.message = '';
      },
    },
  };
  </script>
  
  <style scoped>
  .contact-section {
    max-width: 600px;
    margin: 0 auto;
    padding: 20px;
    border: 1px solid #5e5e5e;
    border-radius: 5px;
    background-color: #333;
  }
  
  .form-group {
    margin-bottom: 15px;
  }
  
  label {
    display: block;
    margin-bottom: 5px;
    font-weight: bold;
  }
  
  input[type="text"],
  textarea {
    width: 100%;
    padding: 10px;
    border: 1px solid #727272;
    border-radius: 4px;
  }
  
  button {
    padding: 10px 15px;
    background-color: #2fb3ff;
    color: white;
    border: none;
    border-radius: 4px;
    cursor: pointer;
  }
  
  button:hover {
    background-color: #1a90d1;
  }
  
  .success-message {
    margin-top: 10px;
    color: green;
    font-weight: bold;
    transition: opacity 0.5s ease-in-out;
  }
  </style>
  