<template>
  <section id="experience" class="experience-section">
    <div class="container">
      <h2 class="section-title">Experience</h2>
      <div class="timeline">
        <div
          v-for="(exp, index) in experiences"
          :key="index"
          class="timeline-item"
        >
          <div class="timeline-marker"></div>
          <div class="timeline-content">
            <h3>{{ exp.role }}</h3>
            <h4>{{ exp.company }}</h4>
            <p class="timeline-date">{{ exp.startDate }} - {{ exp.endDate || 'Present' }}</p>
            <p class="timeline-description">{{ exp.description }}</p>
            <ul v-if="exp.achievements && exp.achievements.length" class="achievements">
              <li v-for="(achievement, i) in exp.achievements" :key="i">{{ achievement }}</li>
            </ul>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
defineProps({
  experiences: {
    type: Array,
    default: () => [
      {
        role: 'Your Role',
        company: 'Company Name',
        startDate: 'Jan 2020',
        endDate: 'Present',
        description: 'Brief description of your responsibilities and achievements.',
        achievements: [
          'Key achievement or responsibility',
          'Another important accomplishment',
          'Notable contribution or project'
        ]
      }
    ]
  }
})
</script>

<style scoped>
.experience-section {
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

.timeline {
  position: relative;
  padding: 2rem 0;
}

.timeline::before {
  content: '';
  position: absolute;
  left: 30px;
  top: 0;
  bottom: 0;
  width: 2px;
  background: linear-gradient(180deg, var(--primary-color), var(--secondary-color));
}

.timeline-item {
  position: relative;
  padding-left: 80px;
  margin-bottom: 3rem;
}

.timeline-marker {
  position: absolute;
  left: 20px;
  top: 0;
  width: 20px;
  height: 20px;
  border-radius: 50%;
  background: var(--primary-color);
  border: 4px solid var(--section-bg);
  box-shadow: 0 0 0 4px var(--primary-color);
}

.timeline-content {
  background: var(--bg-color);
  padding: 2rem;
  border-radius: 10px;
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.08);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.timeline-content:hover {
  transform: translateY(-5px);
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.12);
}

.timeline-content h3 {
  font-size: 1.5rem;
  margin-bottom: 0.5rem;
  color: var(--text-color);
}

.timeline-content h4 {
  font-size: 1.2rem;
  color: var(--primary-color);
  margin-bottom: 0.5rem;
  font-weight: 600;
}

.timeline-date {
  color: var(--text-secondary);
  font-size: 0.9rem;
  margin-bottom: 1rem;
  font-style: italic;
}

.timeline-description {
  color: var(--text-secondary);
  line-height: 1.6;
  margin-bottom: 1rem;
}

.achievements {
  list-style: none;
  padding: 0;
  margin-top: 1rem;
}

.achievements li {
  padding: 0.5rem 0;
  padding-left: 1.5rem;
  position: relative;
  color: var(--text-secondary);
  line-height: 1.6;
}

.achievements li::before {
  content: '▸';
  position: absolute;
  left: 0;
  color: var(--primary-color);
  font-weight: bold;
}

@media (max-width: 768px) {
  .experience-section {
    padding: 4rem 1rem;
  }

  .timeline::before {
    left: 15px;
  }

  .timeline-item {
    padding-left: 50px;
  }

  .timeline-marker {
    left: 5px;
    width: 15px;
    height: 15px;
  }

  .timeline-content {
    padding: 1.5rem;
  }

  .section-title {
    font-size: 2rem;
  }
}
</style>
