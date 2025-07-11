<template>
  <section class="contact-section">
    <div class="container">
      <h2>Контакты</h2>
      
      <div class="contact-content">
        <div class="contact-info">
          <div class="contact-item">
            <i class="fas fa-envelope"></i>
            <a href="mailto:login00200@gmail.com">login00200@gmail.com</a>
          </div>
          
          <div class="contact-item">
            <i class="fas fa-phone"></i>
            <a href="tel:+79958570052">+7 (995) 857-00-52</a>
          </div>
          
          <div class="contact-item">
            <i class="fab fa-vk"></i>
            <a href="https://vk.com/antosian" target="_blank">vk.com/antosian</a>
          </div>
          
          <div class="contact-item">
            <i class="fab fa-telegram"></i>
            <a href="https://t.me/ruant02" target="_blank">@ruant02</a>
          </div>
          
          <div class="contact-item">
            <i class="fas fa-map-marker-alt"></i>
            <span>Пермь, Россия</span>
          </div>
        </div>
        
        <div class="contact-form">
          <h3>Напишите мне</h3>
          <form @submit.prevent="sendMessage">
            <div class="form-group">
              <input type="text" v-model="form.name" placeholder="Ваше имя" required>
            </div>
            
            <div class="form-group">
              <input type="email" v-model="form.email" placeholder="Ваш email" required>
            </div>
            
            <div class="form-group">
              <textarea v-model="form.message" placeholder="Ваше сообщение" required></textarea>
            </div>
            
            <button type="submit" class="submit-btn">Отправить</button>
          </form>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'ContactSection',
  data() {
    return {
      form: {
        name: '',
        email: '',
        message: ''
      }
    }
  },
  methods: {
    sendMessage() {
      // Здесь можно добавить логику отправки формы
      console.log('Сообщение отправлено:', this.form);
      alert('Сообщение отправлено! Я свяжусь с вами в ближайшее время.');
      
      // Очистка формы после отправки
      this.form = {
        name: '',
        email: '',
        message: ''
      };
    }
  }
}
</script>

<style scoped>
.contact-section {
  padding: 4rem 0;
  background-color: #f9f9f9;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 2rem;
}

h2 {
  text-align: center;
  margin-bottom: 3rem;
  color: #2a5298;
  font-size: 2rem;
}

.contact-content {
  display: flex;
  gap: 3rem;
}

.contact-info {
  flex: 1;
}

.contact-form {
  flex: 1;
}

.contact-item {
  display: flex;
  align-items: center;
  margin-bottom: 1.5rem;
}

.contact-item i {
  font-size: 1.2rem;
  width: 30px;
  color: #2a5298;
}

.contact-item a {
  color: #2a5298;
  text-decoration: none;
  transition: opacity 0.3s;
}

.contact-item a:hover {
  opacity: 0.8;
}

.contact-item span {
  color: #333;
}

.contact-form h3 {
  margin-top: 0;
  margin-bottom: 1.5rem;
  color: #2a5298;
}

.form-group {
  margin-bottom: 1.5rem;
}

.form-group input,
.form-group textarea {
  width: 100%;
  padding: 0.8rem 1rem;
  border: 1px solid #ddd;
  border-radius: 5px;
  font-family: inherit;
  font-size: 1rem;
}

.form-group textarea {
  min-height: 150px;
  resize: vertical;
}

.submit-btn {
  background-color: #2a5298;
  color: white;
  border: none;
  padding: 0.8rem 2rem;
  border-radius: 5px;
  cursor: pointer;
  font-size: 1rem;
  transition: background-color 0.3s;
}

.submit-btn:hover {
  background-color: #1e3c72;
}

@media (max-width: 768px) {
  .contact-content {
    flex-direction: column;
  }
  
  .contact-info {
    margin-bottom: 2rem;
  }
}
</style>