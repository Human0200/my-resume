<template>
  <section class="about-section">
    <div class="container">
      <h2>Обо мне</h2>
      <div class="about-content">
        <div class="about-text">
          <p>Техник по информационным системам. Имею хорошие навыки программирования и понимания информационных систем, нацелен на постоянный профессиональный и личностный рост.</p>
          
          <h3>Личные качества:</h3>
          <ul>
            <li>Ответственный и дисциплинированный</li>
            <li>Высокая работоспособность и готовность к обучению</li>
            <li>Способность к самоорганизации и решению задач</li>
            <li>Коммуникативные способности и готовность к работе в команде</li>
            <li>Обладание аналитическим мышлением</li>
          </ul>
        </div>
        
        <div class="about-details">
          <div class="detail-card">
            <h4>Гражданство</h4>
            <p>Россия</p>
          </div>
          
          <div class="detail-card">
            <h4>Разрешение на работу</h4>
            <p>Россия</p>
          </div>
          
          <div class="detail-card">
            <h4>Готовность к переезду</h4>
            <p>Не готов к переезду, готов к редким командировкам</p>
          </div>
          
          <div class="detail-card">
            <h4>Водительские права</h4>
            <p>Категория B, есть автомобиль</p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'AboutSection'
}
</script>

<style scoped>
.about-section {
  padding: 4rem 0;
  background-color: #f9f9f9;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 2rem;
}

h2 {
  font-size: 2rem;
  margin-bottom: 2rem;
  text-align: center;
  color: #2a5298;
}

.about-content {
  display: flex;
  gap: 3rem;
}

.about-text {
  flex: 2;
}

.about-details {
  flex: 1;
  display: grid;
  grid-template-columns: 1fr;
  gap: 1.5rem;
}

.detail-card {
  background: white;
  padding: 1.5rem;
  border-radius: 8px;
  box-shadow: 0 2px 10px rgba(0,0,0,0.05);
}

.detail-card h4 {
  margin-top: 0;
  color: #2a5298;
  font-size: 1.1rem;
}

.detail-card p {
  margin-bottom: 0;
}

ul {
  padding-left: 1.2rem;
}

li {
  margin-bottom: 0.5rem;
}

@media (max-width: 768px) {
  .about-content {
    flex-direction: column;
  }
}
</style>