<template>
  <section class="experience-section">
    <div class="container">
      <h2>Опыт работы</h2>
      <div class="timeline">
        <div v-for="(job, index) in jobs" :key="index" class="timeline-item">
          <div class="timeline-period">
            {{ job.period }}
            <span class="timeline-duration">{{ job.duration }}</span>
          </div>
          <div class="timeline-content">
            <h3>{{ job.position }}</h3>
            <h4>{{ job.company }}</h4>
            <p class="location">{{ job.location }}</p>
            <p class="industry">{{ job.industry }}</p>
            <ul>
              <li v-for="(responsibility, i) in job.responsibilities" :key="i">{{ responsibility }}</li>
            </ul>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'ExperienceSection',
  data() {
    return {
      jobs: [
        {
          period: 'Декабрь 2023 — настоящее время',
          duration: '1 год 8 месяцев',
          position: '1С-Битрикс разработчик',
          company: 'АО Бэкграунд',
          location: 'Пермь, bg59.ru',
          industry: 'Информационные технологии, системная интеграция, интернет',
          responsibilities: [
            'Разработка веб-сайтов на платформе 1С-Битрикс',
            'Создание расширений/приложений для Битрикс24 (облако и коробка) и их поддержка',
            'Программирование на PHP(d7, Crest, bx24phpsdk), JavaScript(jqery, Bootstrap), HTML, CSS',
            'Интеграция с другими системами (CRM, ERP, CMS)',
            'Управление базами данных MySQL',
            'Работа с bitrix Framework, администрирование CentOs/BitrixVm',
            'Настройка Битрикс24: аналитические отчеты, сущности CRM, бизнес-процессы'
          ]
        },
        {
          period: 'Январь 2025 — Май 2025',
          duration: '5 месяцев',
          position: 'Веб-разработчик (WordPress)',
          company: 'VIM IT AGENCY',
          location: 'Минск',
          industry: 'Информационные технологии, системная интеграция, интернет',
          responsibilities: [
            'Разработка и поддержка сайтов на WordPress',
            'Интеграция плагинов: WooCommerce, Contact Form 7, Yoast SEO',
            'Ускорение загрузки сайта (оптимизация изображений, кэширование)',
            'Работа с Elementor',
            'Настройка доменов, SSL-сертификатов'
          ]
        },
        {
          period: 'Июнь 2023 — Январь 2025',
          duration: '1 год 8 месяцев',
          position: 'Асессор/ Специалист по разметке данных',
          company: 'ООО Рокет Проджект',
          location: 'Пермь, trainingdata.solutions',
          industry: 'Информационные технологии, системная интеграция, интернет',
          responsibilities: [
            'Разметка данных вручную: категоризация текста, определение объектов на изображениях',
            'Работа в CVAT, Photoshop',
            'Присвоение каждому примеру обучающей выборки соответствующего ярлыка или класса'
          ]
        },
        {
          period: 'Февраль 2023 — Май 2023',
          duration: '4 месяца',
          position: 'Системный администратор',
          company: 'МАОУ СОШ №6',
          location: 'Пермь',
          industry: 'Образовательные учреждения',
          responsibilities: [
            'Обслуживание школьного сервера',
            'Написание технической документации',
            'Обслуживание школьных компьютеров',
            'Настройка локальных сетей',
            'Удаленное консультирование пользователей'
          ]
        }
      ]
    }
  }
}
</script>

<style scoped>
.experience-section {
  padding: 4rem 0;
  background-color: white;
}

h2 {
  text-align: center;
  margin-bottom: 3rem;
  color: #2a5298;
  font-size: 2rem;
}

.timeline {
  position: relative;
  max-width: 900px;
  margin: 0 auto;
}

.timeline::before {
  content: '';
  position: absolute;
  width: 2px;
  background-color: #2a5298;
  top: 0;
  bottom: 0;
  left: 50%;
  margin-left: -1px;
}

.timeline-item {
  padding: 20px 40px;
  position: relative;
  width: 50%;
  box-sizing: border-box;
}

.timeline-item:nth-child(odd) {
  left: 0;
}

.timeline-item:nth-child(even) {
  left: 50%;
}

.timeline-period {
  padding: 10px 15px;
  background-color: #2a5298;
  color: white;
  border-radius: 5px;
  position: relative;
  margin-bottom: 15px;
  font-weight: bold;
}

.timeline-duration {
  display: block;
  font-size: 0.8rem;
  opacity: 0.8;
  margin-top: 3px;
}

.timeline-item:nth-child(odd) .timeline-period {
  text-align: right;
}

.timeline-item:nth-child(even) .timeline-period {
  text-align: left;
}

.timeline-content {
  padding: 20px;
  background-color: #f9f9f9;
  border-radius: 5px;
  box-shadow: 0 2px 5px rgba(0,0,0,0.1);
}

.timeline-content h3 {
  margin-top: 0;
  color: #2a5298;
}

.timeline-content h4 {
  margin: 5px 0;
  color: #333;
}

.location, .industry {
  font-size: 0.9rem;
  color: #666;
  margin: 5px 0;
}

.timeline-item::after {
  content: '';
  position: absolute;
  width: 20px;
  height: 20px;
  background-color: white;
  border: 4px solid #2a5298;
  border-radius: 50%;
  top: 30px;
  z-index: 1;
}

.timeline-item:nth-child(odd)::after {
  right: -10px;
}

.timeline-item:nth-child(even)::after {
  left: -10px;
}

@media (max-width: 768px) {
  .timeline::before {
    left: 30px;
  }
  
  .timeline-item {
    width: 100%;
    padding-left: 70px;
    padding-right: 25px;
  }
  
  .timeline-item:nth-child(even) {
    left: 0;
  }
  
  .timeline-item:nth-child(odd) .timeline-period,
  .timeline-item:nth-child(even) .timeline-period {
    text-align: left;
  }
  
  .timeline-item::after {
    left: 20px;
  }
  
  .timeline-item:nth-child(even)::after {
    left: 20px;
  }
}
</style>