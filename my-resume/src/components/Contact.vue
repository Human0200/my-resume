<template>
  <section class="contact-section" id="contact">
    <div class="container">
      <h2 class="section-title">Контакты</h2>

      <div class="contact-content">
        <div class="contact-info">
          <div class="contact-item" v-for="(item, index) in contacts" :key="index">
            <div class="icon-wrapper">
              <i :class="item.icon"></i>
            </div>
            <div class="contact-details">
              <a v-if="item.link" :href="item.link" target="_blank" rel="noopener">{{ item.value }}</a>
              <span v-else>{{ item.value }}</span>
              <p class="contact-label">{{ item.label }}</p>
            </div>
          </div>

          <div class="social-links">
            <a 
              v-for="(social, index) in socials" 
              :key="'social-'+index" 
              :href="social.link" 
              target="_blank"
              rel="noopener"
              :aria-label="social.name"
            >
              <i :class="social.icon"></i>
            </a>
          </div>
        </div>

        <div class="contact-form">
          <h3 class="form-title">Напишите мне</h3>
          <form @submit.prevent="sendMessage" class="message-form">
            <div class="form-group" :class="{ 'has-error': errors.name }">
              <input 
                type="text" 
                v-model="form.name" 
                placeholder="Ваше имя" 
                required
                @focus="clearError('name')"
              >
              <span class="error-message" v-if="errors.name">{{ errors.name }}</span>
            </div>

            <div class="form-group" :class="{ 'has-error': errors.email }">
              <input 
                type="email" 
                v-model="form.email" 
                placeholder="Ваш email" 
                required
                @focus="clearError('email')"
              >
              <span class="error-message" v-if="errors.email">{{ errors.email }}</span>
            </div>

            <div class="form-group" :class="{ 'has-error': errors.message }">
              <textarea 
                v-model="form.message" 
                placeholder="Ваше сообщение" 
                required
                @focus="clearError('message')"
              ></textarea>
              <span class="error-message" v-if="errors.message">{{ errors.message }}</span>
            </div>

            <button type="submit" class="submit-btn" :disabled="isSubmitting">
              <span v-if="!isSubmitting">Отправить</span>
              <span v-else class="loading">
                <i class="fas fa-spinner fa-spin"></i> Отправка...
              </span>
            </button>
          </form>
        </div>
      </div>
    </div>

    <!-- Уведомление -->
    <transition name="slide">
      <div
        v-if="notification.show"
        :class="['notification', notification.type]"
        @click="hideNotification"
      >
        {{ notification.message }}
      </div>
    </transition>
  </section>
</template>

<script>
import emailjs from '@emailjs/browser';

export default {
  name: 'ContactSection',
  data() {
    return {
      contacts: [
        { icon: 'fas fa-envelope', value: 'login00200@gmail.com', link: 'mailto:login00200@gmail.com', label: 'Email' },
        { icon: 'fab fa-vk', value: 'vk.com/antosian', link: 'https://vk.com/antosian ', label: 'VKontakte' },
        { icon: 'fab fa-telegram', value: '@ruant02', link: 'https://t.me/ruant02 ', label: 'Telegram' },
        { icon: 'fab fa-github', value: 'github.com/Human00200', link: 'https://github.com/Human0200 ', label: 'GitHub' },
        { icon: 'fas fa-map-marker-alt', value: 'Пермь, Россия', label: 'Местоположение' }
      ],
      socials: [
        { name: 'VKontakte', icon: 'fab fa-vk', link: 'https://vk.com/antosian ' },
        { name: 'Telegram', icon: 'fab fa-telegram', link: 'https://t.me/ruant02 ' },
        { name: 'GitHub', icon: 'fab fa-github', link: 'https://github.com/Human0200' },
        { name: 'Email', icon: 'fas fa-envelope', link: 'mailto:login00200@gmail.com' }
      ],
      form: {
        name: '',
        email: '',
        message: ''
      },
      errors: {
        name: '',
        email: '',
        message: ''
      },
      isSubmitting: false,
      notification: {
        show: false,
        message: '',
        type: 'success'
      }
    };
  },
  methods: {
    validateForm() {
      let isValid = true;

      if (!this.form.name.trim()) {
        this.errors.name = 'Пожалуйста, введите ваше имя';
        isValid = false;
      }

      if (!this.form.email.trim()) {
        this.errors.email = 'Пожалуйста, введите ваш email';
        isValid = false;
      } else if (!/^\S+@\S+\.\S+$/.test(this.form.email)) {
        this.errors.email = 'Пожалуйста, введите корректный email';
        isValid = false;
      }

      if (!this.form.message.trim()) {
        this.errors.message = 'Пожалуйста, введите ваше сообщение';
        isValid = false;
      }

      return isValid;
    },
    clearError(field) {
      this.errors[field] = '';
    },
    showNotification(message, type = 'success') {
      this.notification = {
        show: true,
        message,
        type
      };
      setTimeout(() => {
        this.hideNotification();
      }, 5000);
    },
    hideNotification() {
      this.notification.show = false;
    },
    async sendMessage() {
      if (!this.validateForm()) return;

      this.isSubmitting = true;

      try {
        const templateParams = {
          name: this.form.name,
          email: this.form.email,
          message: this.form.message,
          time: new Date().toLocaleString()
        };

        await emailjs.send(
          'service_uozg6wo',     // Замените на свой Service ID
          'template_as9lc8i',    // Замените на свой Template ID
          templateParams,
          '_qD0EhgsHlYKIYuVn'   // Замените на свой Public Key
        );

        this.showNotification('Сообщение отправлено! Я свяжусь с вами в ближайшее время.');

        // Очистка формы
        this.form = {
          name: '',
          email: '',
          message: ''
        };
      } catch (error) {
        console.error('Ошибка отправки:', error);
        this.showNotification('Произошла ошибка при отправке. Пожалуйста, попробуйте позже.', 'error');
      } finally {
        this.isSubmitting = false;
      }
    }
  }
};
</script>

<style scoped>
/* Основные стили секции */
.contact-section {
  padding: 80px 0;
  background-color: #f9f9f9;
  position: relative;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 20px;
}

.section-title {
  text-align: center;
  font-size: 2.5rem;
  margin-bottom: 60px;
  color: #333;
  position: relative;
}

.section-title::after {
  content: '';
  display: block;
  width: 80px;
  height: 4px;
  background: #3a86ff;
  margin: 15px auto 0;
}

/* Контент контактов */
.contact-content {
  display: flex;
  flex-wrap: wrap;
  gap: 40px;
  justify-content: space-between;
}

.contact-info {
  flex: 1;
  min-width: 300px;
}

.contact-form {
  flex: 1;
  min-width: 300px;
  background: white;
  padding: 30px;
  border-radius: 10px;
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
}

/* Элементы контактов */
.contact-item {
  display: flex;
  align-items: flex-start;
  margin-bottom: 25px;
}

.icon-wrapper {
  font-size: 1.5rem;
  color: #3a86ff;
  margin-right: 20px;
  width: 30px;
  text-align: center;
}

.contact-details {
  flex: 1;
}

.contact-details a {
  color: #333;
  text-decoration: none;
  transition: color 0.3s;
}

.contact-details a:hover {
  color: #3a86ff;
}

.contact-label {
  margin-top: 5px;
  font-size: 0.9rem;
  color: #666;
}

/* Социальные сети */
.social-links {
  display: flex;
  gap: 15px;
  margin-top: 30px;
}

.social-links a {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 40px;
  height: 40px;
  border-radius: 50%;
  background: #f0f0f0;
  color: #333;
  font-size: 1.2rem;
  transition: all 0.3s;
}

.social-links a:hover {
  background: #3a86ff;
  color: white;
  transform: translateY(-3px);
}

/* Форма */
.form-title {
  font-size: 1.8rem;
  margin-bottom: 25px;
  color: #333;
}

.message-form {
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.form-group {
  position: relative;
}

.form-group input,
.form-group textarea {
  width: 100%;
  padding: 12px 15px;
  border: 1px solid #ddd;
  border-radius: 5px;
  font-size: 1rem;
  transition: border-color 0.3s;
}

.form-group textarea {
  min-height: 150px;
  resize: vertical;
}

.form-group input:focus,
.form-group textarea:focus {
  outline: none;
  border-color: #3a86ff;
}

/* Ошибки */
.has-error input,
.has-error textarea {
  border-color: #ff3860;
}

.error-message {
  display: block;
  color: #ff3860;
  font-size: 0.8rem;
  margin-top: 5px;
}

/* Кнопка */
.submit-btn {
  background: #3a86ff;
  color: white;
  border: none;
  padding: 12px 25px;
  font-size: 1rem;
  border-radius: 5px;
  cursor: pointer;
  transition: all 0.3s;
}

.submit-btn:hover {
  background: #2667cc;
  transform: translateY(-2px);
}

.submit-btn:disabled {
  background: #cccccc;
  cursor: not-allowed;
  transform: none;
}

/* Уведомления */
.notification {
  position: fixed;
  bottom: 20px;
  right: 20px;
  padding: 15px 25px;
  border-radius: 5px;
  color: white;
  font-weight: 500;
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
  z-index: 1000;
  cursor: pointer;
  animation: slideIn 0.3s ease-out forwards;
}

.notification.success {
  background-color: #4CAF50;
}

.notification.error {
  background-color: #F44336;
}

/* Анимации */
@keyframes slideIn {
  from {
    transform: translateY(100px);
    opacity: 0;
  }
  to {
    transform: translateY(0);
    opacity: 1;
  }
}

@keyframes slideOut {
  from {
    transform: translateY(0);
    opacity: 1;
  }
  to {
    transform: translateY(100px);
    opacity: 0;
  }
}

.notification-leave-active {
  animation: slideOut 0.3s ease-in forwards;
}

.loading {
  display: inline-flex;
  align-items: center;
}

.loading i {
  margin-right: 8px;
  animation: spin 1s linear infinite;
}

@keyframes spin {
  from { transform: rotate(0deg); }
  to { transform: rotate(360deg); }
}

/* Адаптивность */
@media (max-width: 768px) {
  .contact-content {
    flex-direction: column;
  }
  
  .section-title {
    font-size: 2rem;
    margin-bottom: 40px;
  }
}
</style>