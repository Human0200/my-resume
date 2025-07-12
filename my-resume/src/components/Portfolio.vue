<template>
  <section class="portfolio-section">
    <div class="container">
      <h2>Портфолио</h2>
      
      <div class="portfolio-filter">
        <button 
          v-for="category in categories" 
          :key="category" 
          @click="activeCategory = category"
          :class="{active: activeCategory === category}"
        >
          {{ category }}
        </button>
      </div>
      
      <div class="portfolio-grid">
        <div 
          v-for="(project, index) in filteredProjects" 
          :key="index" 
          class="portfolio-item"
          @click="openModal(project)"
        >
          <div class="portfolio-image">
            <img :src="project.image" :alt="project.title">
          </div>
          <div class="portfolio-overlay">
            <h3>{{ project.title }}</h3>
            <p>{{ project.technology }}</p>
          </div>
        </div>
      </div>
      
      <div v-if="selectedProject" class="portfolio-modal" @click.self="closeModal">
        <div class="modal-content">
          <button class="close-btn" @click="closeModal">&times;</button>
          <h3>{{ selectedProject.title }}</h3>
          <div class="modal-image">
            <img :src="selectedProject.image" :alt="selectedProject.title">
          </div>
          <p class="modal-tech">Технологии: {{ selectedProject.technology }}</p>
          <p class="modal-desc">{{ selectedProject.description }}</p>
          <a :href="selectedProject.link" target="_blank" class="modal-link">Посмотреть проект</a>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'PortfolioSection',
  data() {
    return {
      activeCategory: 'Все',
      selectedProject: null,
      categories: ['Все', 'Bitrix', 'WordPress', 'Vue.js'],
      projects: [
        {
          title: 'Babynails',
          technology: 'Vue.js',
          category: 'Vue.js',
          image: './images/babynails.png',
          description: 'Сайт профессионального мастера по маникюру и педикюру.',
          link: 'https://babynails.ru/'
        },
        {
          title: 'Podocentr',
          technology: 'WordPress',
          category: 'WordPress',
          image: './images/podocentr.png',
          description: 'Сайт медицинского центра с возможностью онлайн-оплаты и блогом.',
          link: 'https://podocentr.by/'
        },
        {
          title: 'Lifepravo',
          technology: 'WordPress',
          category: 'WordPress',
          image: './images/lifepravo.png',
          description: 'Юридический сайт с возможностью оставить заявку на консультацию.',
          link: 'https://lifepravo.ru/'
        },
        {
          title: 'Palmira59',
          technology: '1С-Битрикс',
          category: 'Bitrix',
          image: './images/palmira.png',
          description: 'Сайт попродаже авто-запчастей.',
          link: 'https://palmira59.ru/'
        },
        {
          title: 'Promportal24',
          technology: '1С-Битрикс',
          category: 'Bitrix',
          image: './images/promportal.png',
          description: 'Сайт попродаже оборудования для заводов.',
          link: 'https://promportal24.ru/'
        },
        {
          title: 'GTNT',
          technology: '1С-Битрикс',
          category: 'Bitrix',
          image: './images/gtnt.png',
          description: 'Сайт компании предоставлющей услуги в телекоммуникационной области.',
          link: 'https://gtnt.ru/'
        },
        {
          title: 'Зонд пак',
          technology: '1С-Битрикс',
          category: 'Bitrix',
          image: './images/zond-pak.png',
          description: 'Сайт попродаже собственного оборудования для заводов.',
          link: 'https://zond-pak.bitrix24shop.ru/'
        },
        {
          title: 'Мое резюме',
          technology: 'Vue.js',
          category: 'Vue.js',
          image: './images/myresume.png',
          description: 'Мое резюме.',
          link: 'http://a0922102.xsph.ru/'
        }
      ]
    }
  },
  computed: {
    filteredProjects() {
      if (this.activeCategory === 'Все') {
        return this.projects
      }
      return this.projects.filter(project => project.category === this.activeCategory)
    }
  },
  methods: {
    openModal(project) {
      this.selectedProject = project
      document.body.style.overflow = 'hidden'
    },
    closeModal() {
      this.selectedProject = null
      document.body.style.overflow = 'auto'
    }
  }
}
</script>

<style scoped>
.portfolio-section {
  padding: 4rem 0;
  background-color: white;
}

h2 {
  text-align: center;
  margin-bottom: 3rem;
  color: #2a5298;
  font-size: 2rem;
}

.portfolio-filter {
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
  gap: 0.5rem;
  margin-bottom: 2rem;
}

.portfolio-filter button {
  padding: 0.5rem 1.5rem;
  background: none;
  border: 2px solid #2a5298;
  color: #2a5298;
  border-radius: 30px;
  cursor: pointer;
  font-weight: 600;
  transition: all 0.3s;
}

.portfolio-filter button:hover,
.portfolio-filter button.active {
  background-color: #2a5298;
  color: white;
}

.portfolio-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  gap: 1.5rem;
}

.portfolio-item {
  position: relative;
  border-radius: 8px;
  overflow: hidden;
  cursor: pointer;
  aspect-ratio: 16/9;
  box-shadow: 0 3px 10px rgba(0,0,0,0.1);
  transition: transform 0.3s;
}

.portfolio-item:hover {
  transform: translateY(-5px);
}

.portfolio-image img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.portfolio-overlay {
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  background: linear-gradient(to top, rgba(0,0,0,0.8), transparent);
  color: white;
  padding: 1.5rem;
  opacity: 0;
  transition: opacity 0.3s;
}

.portfolio-item:hover .portfolio-overlay {
  opacity: 1;
}

.portfolio-overlay h3 {
  margin: 0 0 0.5rem;
}

.portfolio-overlay p {
  margin: 0;
  font-size: 0.9rem;
}

.portfolio-modal {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: rgba(0,0,0,0.8);
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 1000;
  padding: 1rem;
}

.modal-content {
  background-color: white;
  max-width: 800px;
  width: 100%;
  border-radius: 8px;
  padding: 2rem;
  position: relative;
  max-height: 90vh;
  overflow-y: auto;
}

.close-btn {
  position: absolute;
  top: 1rem;
  right: 1rem;
  background: none;
  border: none;
  font-size: 1.5rem;
  cursor: pointer;
  color: #666;
}

.modal-content h3 {
  margin-top: 0;
  color: #2a5298;
  font-size: 1.5rem;
}

.modal-image {
  margin: 1.5rem 0;
}

.modal-image img {
  width: 100%;
  border-radius: 5px;
  box-shadow: 0 3px 10px rgba(0,0,0,0.1);
}

.modal-tech {
  font-weight: 600;
  color: #2a5298;
}

.modal-desc {
  margin: 1rem 0;
  line-height: 1.6;
}

.modal-link {
  display: inline-block;
  padding: 0.7rem 1.5rem;
  background-color: #2a5298;
  color: white;
  text-decoration: none;
  border-radius: 5px;
  transition: background-color 0.3s;
}

.modal-link:hover {
  background-color: #1e3c72;
}
</style>