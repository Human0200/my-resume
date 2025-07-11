<template>
  <section class="skills-section">
    <div class="container">
      <h2>Навыки</h2>
      
      <div class="skills-grid">
        <div class="skill-category">
          <h3>Технические навыки</h3>
          <div class="skills-list">
            <div v-for="(skill, index) in technicalSkills" :key="'tech-'+index" class="skill-item">
              <div class="skill-name">{{ skill.name }}</div>
              <div class="skill-bar">
                <div class="skill-level" :style="{width: skill.level + '%'}"></div>
              </div>
            </div>
          </div>
        </div>
        
        <div class="skill-category">
          <h3>Языки программирования</h3>
          <div class="skills-list">
            <div v-for="(skill, index) in programmingLanguages" :key="'prog-'+index" class="skill-item">
              <div class="skill-name">{{ skill.name }}</div>
              <div class="skill-bar">
                <div class="skill-level" :style="{width: skill.level + '%'}"></div>
              </div>
            </div>
          </div>
        </div>
        
        <div class="skill-category">
          <h3>Иностранные языки</h3>
          <div class="skills-list">
            <div v-for="(skill, index) in languageSkills" :key="'lang-'+index" class="skill-item">
              <div class="skill-name">{{ skill.name }}</div>
              <div class="skill-bar">
                <div class="skill-level" :style="{width: skill.level + '%'}"></div>
              </div>
            </div>
          </div>
        </div>
      </div>
      
      <div class="other-skills">
        <h3>Другие навыки</h3>
        <div class="tags">
          <span v-for="(skill, index) in otherSkills" :key="'other-'+index" class="tag">{{ skill }}</span>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'SkillsSection',
  data() {
    return {
      technicalSkills: [
        { name: '1С-Битрикс', level: 85 },
        { name: 'WordPress', level: 75 },
        { name: 'Git', level: 80 },
        { name: 'Docker', level: 70 },
        { name: 'MySQL', level: 80 },
        { name: 'Linux', level: 65 }
      ],
      programmingLanguages: [
        { name: 'PHP', level: 85 },
        { name: 'JavaScript', level: 75 },
        { name: 'HTML/CSS', level: 90 },
        { name: 'C#', level: 60 },
        { name: 'Python', level: 50 },
        { name: 'SQL', level: 80 }
      ],
      languageSkills: [
        { name: 'Русский', level: 100 },
        { name: 'Английский (B1)', level: 60 }
      ],
      otherSkills: [
        'MS Office', 'Active Directory', 'Windows Server', 'Unity', 
        'Blender3D', 'CVAT', 'Photoshop', 'Bootstrap', 'jQuery',
        'API', 'Bitrix Framework', 'Elementor', 'WooCommerce'
      ]
    }
  }
}
</script>

<style scoped>
.skills-section {
  padding: 4rem 0;
  background-color: #f9f9f9;
}

h2 {
  text-align: center;
  margin-bottom: 3rem;
  color: #2a5298;
  font-size: 2rem;
}

.skills-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 2rem;
  margin-bottom: 3rem;
}

.skill-category {
  background: white;
  padding: 1.5rem;
  border-radius: 8px;
  box-shadow: 0 2px 10px rgba(0,0,0,0.05);
}

.skill-category h3 {
  margin-top: 0;
  color: #2a5298;
  font-size: 1.3rem;
  margin-bottom: 1.5rem;
}

.skill-item {
  margin-bottom: 1rem;
}

.skill-name {
  margin-bottom: 0.3rem;
  font-weight: 500;
}

.skill-bar {
  height: 8px;
  background-color: #eee;
  border-radius: 4px;
  overflow: hidden;
}

.skill-level {
  height: 100%;
  background: linear-gradient(90deg, #2a5298, #1e3c72);
  border-radius: 4px;
}

.other-skills {
  background: white;
  padding: 1.5rem;
  border-radius: 8px;
  box-shadow: 0 2px 10px rgba(0,0,0,0.05);
}

.other-skills h3 {
  margin-top: 0;
  color: #2a5298;
  font-size: 1.3rem;
  margin-bottom: 1.5rem;
}

.tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
}

.tag {
  background-color: #e0e9f9;
  color: #2a5298;
  padding: 0.5rem 1rem;
  border-radius: 20px;
  font-size: 0.9rem;
}
</style>