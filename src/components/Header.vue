<template>
  <header class="header" :class="{ scrolled: isScrolled }">
    <nav class="nav">
      <div class="nav-brand">
        <a href="#home" @click.prevent="scrollTo('home')">Joseph Dodd</a>
      </div>
      <ul class="nav-links">
        <li><a href="#about" @click.prevent="scrollTo('about')">About</a></li>
        <li>
          <a href="#experience" @click.prevent="scrollTo('experience')"
            >Experience</a
          >
        </li>
        <li>
          <a href="#projects" @click.prevent="scrollTo('projects')">Projects</a>
        </li>
        <li>
          <a href="#skills" @click.prevent="scrollTo('skills')">Skills</a>
        </li>
        <li>
          <button
            class="theme-toggle"
            @click="$emit('toggle-theme')"
            :aria-label="
              theme === 'dark' ? 'Switch to light mode' : 'Switch to dark mode'
            "
          >
            <span v-if="theme === 'dark'">☀️</span>
            <span v-else>🌙</span>
          </button>
        </li>
      </ul>
      <button
        class="mobile-menu-toggle"
        @click="toggleMobileMenu"
        :aria-label="isMobileMenuOpen ? 'Close menu' : 'Open menu'"
        :aria-expanded="isMobileMenuOpen"
      >
        <span
          class="hamburger-line"
          :class="{ active: isMobileMenuOpen }"
        ></span>
        <span
          class="hamburger-line"
          :class="{ active: isMobileMenuOpen }"
        ></span>
        <span
          class="hamburger-line"
          :class="{ active: isMobileMenuOpen }"
        ></span>
      </button>
    </nav>
    <div class="mobile-menu" :class="{ open: isMobileMenuOpen }">
      <ul class="mobile-nav-links">
        <li>
          <a href="#about" @click.prevent="handleMobileLinkClick('about')"
            >About</a
          >
        </li>
        <li>
          <a
            href="#experience"
            @click.prevent="handleMobileLinkClick('experience')"
            >Experience</a
          >
        </li>
        <li>
          <a href="#projects" @click.prevent="handleMobileLinkClick('projects')"
            >Projects</a
          >
        </li>
        <li>
          <a href="#skills" @click.prevent="handleMobileLinkClick('skills')"
            >Skills</a
          >
        </li>
        <li>
          <button
            class="theme-toggle mobile"
            @click="$emit('toggle-theme')"
            :aria-label="
              theme === 'dark' ? 'Switch to light mode' : 'Switch to dark mode'
            "
          >
            <span v-if="theme === 'dark'">☀️</span>
            <span v-else>🌙</span>
            <span class="theme-toggle-text">Toggle Theme</span>
          </button>
        </li>
      </ul>
    </div>
    <div class="hero-section">
      <div class="hero-content">
        <div class="hero-text">
          <h1 class="hero-title">{{ name }}</h1>
          <p class="hero-tagline">
            {{ tagline }}
          </p>
          <div class="hero-actions">
            <a
              href="#about"
              @click.prevent="scrollTo('about')"
              class="hero-button primary"
              >Learn More</a
            >
            <a
              href="#projects"
              @click.prevent="scrollTo('projects')"
              class="hero-button secondary"
              >View Projects</a
            >
          </div>
        </div>
        <div class="hero-image">
          <div class="hero-placeholder">
            <img :src="profileImage" alt="Joseph Dodd" class="profile-image" />
          </div>
        </div>
      </div>
    </div>
  </header>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from "vue";
import profileImage from "@/assets/images/joeFlorence.jpeg";

defineProps({
  theme: {
    type: String,
    default: "light",
  },
  name: {
    type: String,
    default: "Your Name",
  },
  jobTitle: {
    type: String,
    default: "Developer",
  },
  tagline: {
    type: String,
    default: "",
  },
});

defineEmits(["toggle-theme"]);

const isScrolled = ref(false);
const isMobileMenuOpen = ref(false);

const handleScroll = () => {
  isScrolled.value = window.scrollY > 100;
};

const scrollTo = (sectionId) => {
  const element = document.getElementById(sectionId);
  if (element) {
    element.scrollIntoView({ behavior: "smooth", block: "start" });
  }
};

const toggleMobileMenu = () => {
  isMobileMenuOpen.value = !isMobileMenuOpen.value;
};

const handleMobileLinkClick = (sectionId) => {
  scrollTo(sectionId);
  isMobileMenuOpen.value = false;
};

onMounted(() => {
  window.addEventListener("scroll", handleScroll);
});

onUnmounted(() => {
  window.removeEventListener("scroll", handleScroll);
});
</script>

<style scoped>
.header {
  position: relative;
  z-index: 1000;
  background: var(--bg-color);
  transition: all 0.3s ease;
}

.header .nav {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  background: rgba(255, 255, 255, 0.95);
  backdrop-filter: blur(10px);
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.05);
  transition: all 0.3s ease;
}

[data-theme="dark"] .header .nav {
  background: rgba(17, 24, 39, 0.95);
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.3);
}

.header.scrolled .nav {
  box-shadow: 0 2px 20px rgba(0, 0, 0, 0.1);
}

[data-theme="dark"] .header.scrolled .nav {
  box-shadow: 0 2px 20px rgba(0, 0, 0, 0.5);
}

.nav {
  max-width: 100%;
  margin: 0 auto;
  padding: 1rem 2rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
  min-height: 70px;
}

.nav-brand a {
  font-size: 1.5rem;
  font-weight: 700;
  color: var(--primary-color);
  text-decoration: none;
  transition: color 0.3s ease;
}

.nav-brand a:hover {
  color: var(--primary-hover);
}

.nav-links {
  display: flex;
  list-style: none;
  gap: 2rem;
  margin: 0;
  padding: 0;
  align-items: center;
}

.nav-links a {
  color: var(--text-color);
  text-decoration: none;
  font-weight: 500;
  transition: color 0.3s ease;
  position: relative;
}

.nav-links a::after {
  content: "";
  position: absolute;
  bottom: -5px;
  left: 0;
  width: 0;
  height: 2px;
  background: var(--primary-color);
  transition: width 0.3s ease;
}

.nav-links a:hover {
  color: var(--primary-color);
}

.nav-links a:hover::after {
  width: 100%;
}

.theme-toggle {
  background: transparent;
  border: 2px solid var(--primary-color);
  color: var(--primary-color);
  padding: 0.5rem 0.75rem;
  border-radius: 8px;
  cursor: pointer;
  font-size: 1.2rem;
  transition: all 0.3s ease;
  display: flex;
  align-items: center;
  justify-content: center;
}

.theme-toggle:hover {
  background: var(--primary-color);
  color: white;
  transform: scale(1.1);
}

.mobile-menu-toggle {
  display: none;
  flex-direction: column;
  gap: 5px;
  background: transparent;
  border: none;
  cursor: pointer;
  padding: 0.5rem;
  z-index: 1001;
}

.hamburger-line {
  width: 25px;
  height: 3px;
  background: var(--text-color);
  border-radius: 3px;
  transition: all 0.3s ease;
}

.hamburger-line.active:nth-child(1) {
  transform: rotate(45deg) translate(8px, 8px);
}

.hamburger-line.active:nth-child(2) {
  opacity: 0;
}

.hamburger-line.active:nth-child(3) {
  transform: rotate(-45deg) translate(7px, -7px);
}

.mobile-menu {
  position: fixed;
  top: 70px;
  left: 0;
  right: 0;
  background: var(--bg-color);
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
  max-height: 0;
  overflow: hidden;
  transition: max-height 0.3s ease, opacity 0.3s ease;
  opacity: 0;
  z-index: 999;
}

[data-theme="dark"] .mobile-menu {
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.5);
}

.mobile-menu.open {
  max-height: 400px;
  opacity: 1;
}

.mobile-nav-links {
  list-style: none;
  margin: 0;
  padding: 1rem 0;
  display: flex;
  flex-direction: column;
}

.mobile-nav-links li {
  border-bottom: 1px solid var(--border-color);
}

.mobile-nav-links li:last-child {
  border-bottom: none;
}

.mobile-nav-links a {
  display: block;
  padding: 1rem 2rem;
  color: var(--text-color);
  text-decoration: none;
  font-weight: 500;
  transition: all 0.3s ease;
}

.mobile-nav-links a:hover {
  background: var(--section-bg);
  color: var(--primary-color);
  padding-left: 2.5rem;
}

.mobile-nav-links .theme-toggle.mobile {
  width: 100%;
  justify-content: flex-start;
  padding: 1rem 2rem;
  border-radius: 0;
  border: none;
  border-bottom: 1px solid var(--border-color);
  background: transparent;
  text-align: left;
}

.mobile-nav-links .theme-toggle.mobile:hover {
  background: var(--section-bg);
  transform: none;
  padding-left: 2.5rem;
}

.theme-toggle-text {
  margin-left: 0.5rem;
  font-size: 1rem;
}

.hero-section {
  padding: 8rem 2rem 4rem;
  background: linear-gradient(
    135deg,
    var(--section-bg) 0%,
    var(--bg-color) 100%
  );
  min-height: 80vh;
  display: flex;
  align-items: center;
  margin-top: 70px;
}

.hero-content {
  max-width: 1200px;
  margin: 0 auto;
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 4rem;
  align-items: center;
}

.hero-text {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.hero-title {
  font-size: 4rem;
  font-weight: 800;
  background: linear-gradient(
    135deg,
    var(--primary-color),
    var(--secondary-color)
  );
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  line-height: 1.1;
  margin: 0;
}

.hero-tagline {
  font-size: 1.5rem;
  color: var(--text-secondary);
  line-height: 1.6;
  margin: 0;
}

.hero-actions {
  display: flex;
  gap: 1rem;
  margin-top: 1rem;
}

.hero-button {
  padding: 1rem 2rem;
  border-radius: 8px;
  text-decoration: none;
  font-weight: 600;
  transition: all 0.3s ease;
  display: inline-block;
}

.hero-button.primary {
  background: linear-gradient(
    135deg,
    var(--primary-color),
    var(--secondary-color)
  );
  color: white;
  border: none;
}

.hero-button.primary:hover {
  transform: translateY(-2px);
  box-shadow: 0 10px 25px rgba(99, 102, 241, 0.3);
}

.hero-button.secondary {
  background: transparent;
  color: var(--primary-color);
  border: 2px solid var(--primary-color);
}

.hero-button.secondary:hover {
  background: var(--primary-color);
  color: white;
  transform: translateY(-2px);
}

.hero-image {
  display: flex;
  justify-content: center;
  align-items: center;
}

.hero-placeholder {
  width: 100%;
  max-width: 400px;
  aspect-ratio: 1;
  animation: float 6s ease-in-out infinite;
}

@keyframes float {
  0%,
  100% {
    transform: translateY(0px);
  }
  50% {
    transform: translateY(-20px);
  }
}

.profile-image {
  width: 100%;
  height: 100%;
  object-fit: cover;
  border-radius: 50%;
  filter: drop-shadow(0 10px 30px rgba(99, 102, 241, 0.3));
}

@media (max-width: 768px) {
  .nav {
    padding: 1rem;
  }

  .nav-links {
    display: none;
  }

  .mobile-menu-toggle {
    display: flex;
  }

  .nav-brand a {
    font-size: 1.2rem;
  }

  .hero-section {
    padding: 6rem 1rem 3rem;
    min-height: auto;
  }

  .hero-content {
    grid-template-columns: 1fr;
    gap: 2rem;
    text-align: center;
  }

  .hero-title {
    font-size: 2.5rem;
  }

  .hero-tagline {
    font-size: 1.2rem;
  }

  .hero-actions {
    flex-direction: column;
    align-items: stretch;
  }

  .hero-button {
    text-align: center;
  }
}
</style>
