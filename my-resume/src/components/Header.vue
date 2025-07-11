<template>
  <header class="header">
    <div class="header-content">
      <div class="profile-image">
        <img src="/images/profile.jpg" alt="Русаков Антон Сергеевич">
      </div>
      <div class="profile-info">
        <h1>Русаков Антон Сергеевич</h1>
        <p class="subtitle">Fullstack-разработчик</p>
        
        <div class="info-grid">
          <div class="info-item">
            <i class="fas fa-birthday-cake"></i>
            <span>23 года</span>
          </div>
          <div class="info-item">
            <i class="fas fa-envelope"></i>
            <a href="mailto:login00200@gmail.com">login00200@gmail.com</a>
          </div>
          <div class="info-item">
            <i class="fas fa-map-marker-alt"></i>
            <span>Пермь, Россия</span>
          </div>
          <div class="info-item">
            <i class="fab fa-vk"></i>
            <a href="https://vk.com/antosian" target="_blank">vk.com/antosian</a>
          </div>
          <div class="info-item">
            <i class="fab fa-github"></i>
            <a href="https://github.com/Human0200" target="_blank">Human00200</a>
          </div>
          <div class="info-item">
            <i class="fab fa-telegram"></i>
            <a href="https://t.me/ruant02" target="_blank">@ruant02</a>
          </div>
        </div>
      </div>
    </div>
  </header>
</template>

<script>
export default {
  name: 'HeaderSection'
}
</script>

<style scoped>
.header {
  background: linear-gradient(135deg, #1e3c72 0%, #2a5298 100%);
  color: white;
  padding: 2rem 0;
}

.header-content {
  display: flex;
  max-width: 1200px;
  margin: 0 auto;
  align-items: center;
  padding: 0 2rem;
}

.profile-image {
  width: 200px;
  height: 200px;
  border-radius: 50%;
  overflow: hidden;
  border: 4px solid white;
  box-shadow: 0 5px 15px rgba(0,0,0,0.2);
}

.profile-image img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.profile-info {
  margin-left: 3rem;
  flex: 1;
}

.profile-info h1 {
  font-size: 2.5rem;
  margin-bottom: 0.5rem;
}

.subtitle {
  font-size: 1.2rem;
  opacity: 0.9;
  margin-bottom: 1.5rem;
}

.info-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 1rem;
}

.info-item {
  display: flex;
  align-items: center;
  margin-bottom: 0.5rem;
}

.info-item i {
  margin-right: 0.8rem;
  width: 20px;
  text-align: center;
  font-size: 1.1rem;
}

.info-item a {
  color: white;
  text-decoration: none;
  transition: opacity 0.3s;
}

.info-item a:hover {
  opacity: 0.8;
  text-decoration: underline;
}

@media (max-width: 768px) {
  .header-content {
    flex-direction: column;
    text-align: center;
  }
  
  .profile-info {
    margin-left: 0;
    margin-top: 2rem;
  }
  
  .info-grid {
    grid-template-columns: 1fr;
  }
  
  .info-item {
    justify-content: center;
  }
}

/* Анимация иконок при наведении */
.info-item i {
  transition: transform 0.3s;
}

.info-item:hover i {
  transform: scale(1.2);
}

.fab.fa-github {
  color: #f5f5f5; /* Светлый цвет для GitHub */
}

.fab.fa-telegram {
  color: #0088cc; /* Брендовый цвет Telegram */
}

.fab.fa-vk {
  color: #4a76a8; /* Брендовый цвет VK */
}
</style>