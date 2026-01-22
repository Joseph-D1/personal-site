<template>
  <footer class="footer">
    <div class="container">
      <div class="footer-content">
        <p>&copy; {{ currentYear }} {{ name }}. All rights reserved.</p>
        <div class="footer-links">
          <a v-if="email" :href="`mailto:${email}`" class="footer-link"
            >Email</a
          >
          <a
            v-if="linkedin"
            :href="linkedin"
            target="_blank"
            class="footer-link"
            >LinkedIn</a
          >
          <a v-if="github" :href="github" target="_blank" class="footer-link"
            >GitHub</a
          >
          <a v-if="twitter" :href="twitter" target="_blank" class="footer-link"
            >Twitter</a
          >
        </div>
      </div>
    </div>
  </footer>
</template>

<script setup>
import { computed } from "vue";

const props = defineProps({
  name: {
    type: String,
    default: "Your Name",
  },
  email: {
    type: String,
    default: "",
  },
  linkedin: {
    type: String,
    default: "",
  },
  github: {
    type: String,
    default: "",
  },
  twitter: {
    type: String,
    default: "",
  },
});

const currentYear = computed(() => new Date().getFullYear());
</script>

<style scoped>
.footer {
  background: var(--bg-color);
  color: var(--text-color);
  padding: 2rem;
  margin-top: 4rem;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
}

.footer-content {
  display: flex;
  justify-content: space-between;
  align-items: center;
  flex-wrap: wrap;
  gap: 1rem;
}

.footer-links {
  display: flex;
  gap: 2rem;
}

.footer-link {
  color: var(--text-color);
  text-decoration: none;
  transition: color 0.3s ease;
}

.footer-link:hover {
  color: var(--primary-color);
}

@media (max-width: 768px) {
  .footer-content {
    flex-direction: column;
    text-align: center;
  }

  .footer-links {
    gap: 1.5rem;
  }
}
</style>
