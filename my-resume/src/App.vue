<template>
  <div id="app">
    <!-- Анимированный фон -->
    <div class="background-animation">
      <div class="particles"></div>
      <div class="gradient"></div>
    </div>
    
    <!-- Основное содержимое -->
    <div class="content-wrapper">
      <HeaderSection />
      <AboutSection />
      <ExperienceSection />
      <SkillsSection />
      <PortfolioSection />
      <ContactSection />
      
      <footer class="footer">
        <div class="container">
          <p>&copy; {{ currentYear }} Русаков Антон Сергеевич</p>
          <div class="social-links">
            <a href="https://vk.com/antosian" target="_blank"><i class="fab fa-vk"></i></a>
            <a href="mailto:login00200@gmail.com"><i class="fas fa-envelope"></i></a>
          </div>
        </div>
      </footer>
    </div>
  </div>
</template>

<script>
import HeaderSection from './components/Header.vue'
import AboutSection from './components/About.vue'
import ExperienceSection from './components/Experience.vue'
import SkillsSection from './components/Skills.vue'
import PortfolioSection from './components/Portfolio.vue'
import ContactSection from './components/Contact.vue'

export default {
  name: 'App',
  components: {
    HeaderSection,
    AboutSection,
    ExperienceSection,
    SkillsSection,
    PortfolioSection,
    ContactSection
  },
  computed: {
    currentYear() {
      return new Date().getFullYear()
    }
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@300;400;500;700&display=swap');
@import url('https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.4/css/all.min.css');

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: 'Roboto', sans-serif;
  line-height: 1.6;
  color: #333;
  overflow-x: hidden;
  background-color: #f5f7fa;
}

#app {
  position: relative;
  min-height: 100vh;
  display: flex;
  flex-direction: column;
}

/* Анимированный фон */
.background-animation {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: -1;
  overflow: hidden;
}

/* Частицы - теперь остаются в пределах экрана */
.particles {
  position: absolute;
  top: -10%;
  left: -10%;
  width: 120%;
  height: 120%;
  background-image: url("data:image/svg+xml,%3Csvg width='60' height='60' viewBox='0 0 60 60' xmlns='http://www.w3.org/2000/svg'%3E%3Cg fill='%232a5298' fill-opacity='0.08' fill-rule='evenodd'%3E%3Ccircle cx='10' cy='10' r='3'/%3E%3Ccircle cx='40' cy='40' r='3'/%3E%3C/g%3E%3C/svg%3E");
  animation: particles-move 40s linear infinite;
}

/* Плавная циклическая анимация частиц */
@keyframes particles-move {
  0% {
    transform: translate(0, 0);
  }
  25% {
    transform: translate(-5%, 5%);
  }
  50% {
    transform: translate(-10%, 0);
  }
  75% {
    transform: translate(-5%, -5%);
  }
  100% {
    transform: translate(0, 0);
  }
}

/* Градиентная анимация */
.gradient {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: 
    radial-gradient(circle at 20% 30%, rgba(42, 82, 152, 0.05) 0%, transparent 30%),
    radial-gradient(circle at 80% 70%, rgba(30, 60, 114, 0.05) 0%, transparent 30%);
  animation: gradient-move 25s ease infinite alternate;
}

@keyframes gradient-move {
  0% {
    transform: scale(1);
    opacity: 0.8;
  }
  50% {
    transform: scale(1.1);
    opacity: 0.5;
  }
  100% {
    transform: scale(1);
    opacity: 0.8;
  }
}

/* Контент поверх фона */
.content-wrapper {
  position: relative;
  z-index: 1;
  flex: 1;
  display: flex;
  flex-direction: column;
  background-color: rgba(255, 255, 255, 0.95);
  box-shadow: 0 0 30px rgba(0, 0, 0, 0.05);
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 2rem;
}

.footer {
  background-color: #2a5298;
  color: white;
  padding: 2rem 0;
  margin-top: auto;
}

.footer .container {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.social-links {
  display: flex;
  gap: 1.5rem;
}

.social-links a {
  color: white;
  font-size: 1.5rem;
  transition: all 0.3s;
}

.social-links a:hover {
  transform: translateY(-2px);
  opacity: 0.9;
}

@media (max-width: 768px) {
  .footer .container {
    flex-direction: column;
    text-align: center;
    gap: 1rem;
  }
  
  .particles {
    animation-duration: 60s;
  }
}

/* Анимации появления секций */
section {
  opacity: 0;
  transform: translateY(20px);
  animation: fadeInUp 0.8s ease forwards;
}

@keyframes fadeInUp {
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

/* Последовательное появление секций */
.HeaderSection { animation-delay: 0.1s; }
.AboutSection { animation-delay: 0.3s; }
.ExperienceSection { animation-delay: 0.5s; }
.SkillsSection { animation-delay: 0.7s; }
.PortfolioSection { animation-delay: 0.9s; }
.ContactSection { animation-delay: 1.1s; }
</style>