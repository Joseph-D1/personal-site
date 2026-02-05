<template>
  <section id="about" class="about-section">
    <div class="container">
      <h2 class="section-title">Who am I?</h2>
      <div class="about-sections">
        <div class="about-card personal">
          <div>
            <h4 class="card-title">
              <div class="card-icon">👤</div>
              I love learning new things, and developing myself.
            </h4>
          </div>
          <p class="card-content">{{ personalAbout }}</p>
        </div>
        <div class="about-card professional">
          <h4 class="card-title">
            <div class="card-icon">💼</div>
            I have experience in web development and cloud infrastructure.
          </h4>
          <p class="card-content">{{ professionalAbout }}</p>
        </div>
      </div>
      <div class="about-image" v-if="imageUrl">
        <img :src="imageUrl" :alt="name" />
      </div>
      <div class="intro-header">
        <p>Get in touch with me!</p>
        <div class="contact-info">
          <a :href="`mailto:${email}`" class="contact-link">
            <span>📧</span> {{ email }}
          </a>
          <a
            v-if="linkedin"
            :href="linkedin"
            target="_blank"
            class="contact-link"
          >
            <span>💼</span> LinkedIn
          </a>
          <a v-if="github" :href="github" target="_blank" class="contact-link">
            <span>💻</span> GitHub
          </a>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
defineProps({
  name: {
    type: String,
    default: "Your Name",
  },
  jobTitle: {
    type: String,
    default: "Your Job Title",
  },
  email: {
    type: String,
    default: "your.email@example.com",
  },
  linkedin: {
    type: String,
    default: "",
  },
  github: {
    type: String,
    default: "",
  },
  imageUrl: {
    type: String,
    default: "",
  },
  personalAbout: {
    type: String,
    default: "",
  },
  professionalAbout: {
    type: String,
    default: "",
  },
});
</script>

<style scoped>
.about-section {
  padding: 4rem 2rem;
  background: var(--bg-color);
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  text-align: center;
}

.section-title {
  font-size: 2.5rem;
  margin-bottom: 4rem;
  text-align: center;
  color: var(--text-color);
  position: relative;
  display: inline-block;
  width: 100%;
}

.section-title::after {
  content: "";
  position: absolute;
  bottom: -20px;
  left: 50%;
  transform: translateX(-50%);
  width: 60px;
  height: 4px;
  background: linear-gradient(
    90deg,
    var(--primary-color),
    var(--secondary-color)
  );
  border-radius: 2px;
}

.intro-header {
  margin-bottom: 4rem;
  padding-bottom: 2rem;
}

.name {
  font-size: 2.5rem;
  margin-bottom: 0.5rem;
  color: var(--text-color);
  font-weight: 700;
}

.job-title {
  font-size: 1.5rem;
  color: var(--primary-color);
  margin-bottom: 2rem;
  font-weight: 600;
}

.contact-info {
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
  gap: 2rem;
  margin-top: 2rem;
}

.contact-link {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  color: var(--text-color);
  text-decoration: none;
  transition: all 0.3s ease;
  font-size: 1rem;
  padding: 0.5rem 1rem;
  border-radius: 8px;
  background: var(--section-bg);
}

.contact-link:hover {
  color: var(--primary-color);
  background: var(--primary-color);
  color: white;
  transform: translateY(-2px);
}

.about-sections {
  display: grid;
  grid-template-rows: repeat(auto-fit, minmax(300px, 1fr));
  gap: 2rem;
  margin-bottom: 3rem;
  max-width: 100%;
  margin-left: auto;
  margin-right: auto;
}

.about-card {
  background: var(--section-bg);
  padding: 2.5rem 2rem;
  border-radius: 20px;
  box-shadow: 0 5px 20px rgba(0, 0, 0, 0.08);
  transition: all 0.3s ease;
  text-align: left;
  position: relative;
  overflow: hidden;
}

.about-card::before {
  content: "";
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  height: 4px;
  background: linear-gradient(
    90deg,
    var(--primary-color),
    var(--secondary-color)
  );
}

.about-card:hover {
  /* transform: translateY(-10px); */
  box-shadow: 0 15px 40px rgba(0, 0, 0, 0.15);
}

.card-icon {
  font-size: 3rem;
  margin-bottom: 1rem;
  padding: 0 1rem 0 0;
  display: inline-block;
}

.card-title {
  font-size: 1.5rem;
  margin-bottom: 1.5rem;
  color: var(--text-color);
  font-weight: 700;
  text-align: left;
  /* text-transform: uppercase; */
  /* letter-spacing: 1px; */
}

.card-content {
  font-size: 1.1rem;
  line-height: 1.8;
  color: var(--text-secondary);
  /* text-align: left; */
}

.about-image {
  text-align: center;
  margin-top: 3rem;
}

.about-image img {
  width: 100%;
  max-width: 400px;
  height: auto;
  border-radius: 20px;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
}

@media (max-width: 768px) {
  .about-section {
    padding: 4rem 1rem;
  }

  .section-title {
    font-size: 2rem;
  }

  .name {
    font-size: 2rem;
  }

  .job-title {
    font-size: 1.2rem;
  }

  .about-sections {
    grid-template-columns: 1fr;
    gap: 1.5rem;
  }

  .about-card {
    padding: 2rem 1.5rem;
  }

  .card-title {
    font-size: 1.3rem;
  }

  .card-content {
    font-size: 1rem;
  }

  .contact-info {
    flex-direction: column;
    gap: 1rem;
    align-items: center;
  }
}
</style>
