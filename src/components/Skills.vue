<template>
  <section id="skills" class="skills-section">
    <div class="container">
      <h2 class="section-title">Skills</h2>
      <div class="skills-container">
        <div
          v-for="(category, index) in skillCategories"
          :key="index"
          class="skill-category"
        >
          <h3>{{ category.name }}</h3>
          <div class="skills-list">
            <div
              v-for="(skill, i) in category.skills"
              :key="i"
              class="skill-item"
            >
              <span class="skill-name">{{ skill.name }}</span>
              <div class="skill-bar">
                <div
                  class="skill-progress"
                  :style="{ width: skill.level + '%' }"
                ></div>
              </div>
              <span class="skill-level">{{ skill.level }}%</span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
defineProps({
  skillCategories: {
    type: Array,
    default: () => [
      {
        name: 'Frontend',
        skills: [
          { name: 'Vue.js', level: 90 },
          { name: 'JavaScript', level: 85 },
          { name: 'HTML/CSS', level: 95 },
          { name: 'React', level: 75 }
        ]
      },
      {
        name: 'Backend',
        skills: [
          { name: 'Node.js', level: 80 },
          { name: 'Python', level: 75 },
          { name: 'Database', level: 70 }
        ]
      },
      {
        name: 'Tools & Others',
        skills: [
          { name: 'Git', level: 85 },
          { name: 'Docker', level: 60 },
          { name: 'AWS', level: 65 }
        ]
      }
    ]
  }
})
</script>

<style scoped>
.skills-section {
  padding: 4rem 2rem;
  background: var(--section-bg);
}

.container {
  max-width: 1200px;
  margin: 0 auto;
}

.section-title {
  font-size: 2.5rem;
  margin-bottom: 3rem;
  text-align: center;
  color: var(--text-color);
  position: relative;
  display: inline-block;
  width: 100%;
}

.section-title::after {
  content: '';
  position: absolute;
  bottom: -10px;
  left: 50%;
  transform: translateX(-50%);
  width: 60px;
  height: 4px;
  background: linear-gradient(90deg, var(--primary-color), var(--secondary-color));
  border-radius: 2px;
}

.skills-container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 3rem;
}

.skill-category {
  background: var(--bg-color);
  padding: 2rem;
  border-radius: 15px;
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.08);
}

.skill-category h3 {
  font-size: 1.5rem;
  margin-bottom: 1.5rem;
  color: var(--text-color);
  text-align: center;
  padding-bottom: 1rem;
  border-bottom: 2px solid var(--primary-color);
}

.skills-list {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.skill-item {
  display: grid;
  grid-template-columns: 1fr auto;
  grid-template-rows: auto auto;
  gap: 0.5rem;
  align-items: center;
}

.skill-name {
  font-weight: 500;
  color: var(--text-color);
  grid-column: 1;
  grid-row: 1;
}

.skill-level {
  font-size: 0.9rem;
  color: var(--text-secondary);
  grid-column: 2;
  grid-row: 1;
}

.skill-bar {
  grid-column: 1 / -1;
  grid-row: 2;
  height: 8px;
  background: var(--section-bg);
  border-radius: 10px;
  overflow: hidden;
  position: relative;
}

.skill-progress {
  height: 100%;
  background: linear-gradient(90deg, var(--primary-color), var(--secondary-color));
  border-radius: 10px;
  transition: width 1s ease;
  animation: slideIn 1s ease;
}

@keyframes slideIn {
  from {
    width: 0;
  }
}

@media (max-width: 768px) {
  .skills-section {
    padding: 4rem 1rem;
  }

  .skills-container {
    grid-template-columns: 1fr;
    gap: 2rem;
  }

  .section-title {
    font-size: 2rem;
  }
}
</style>
