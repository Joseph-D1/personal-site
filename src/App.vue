<script setup>
import { ref, onMounted } from "vue";
import Header from "./components/Header.vue";
import About from "./components/About.vue";
import Experience from "./components/Experience.vue";
import Projects from "./components/Projects.vue";
import Skills from "./components/Skills.vue";
import Footer from "./components/Footer.vue";

// Theme management
const theme = ref("light");

const getSystemTheme = () => {
  if (
    window.matchMedia &&
    window.matchMedia("(prefers-color-scheme: dark)").matches
  ) {
    return "dark";
  }
  return "light";
};

const applyTheme = (newTheme) => {
  theme.value = newTheme;
  document.documentElement.setAttribute("data-theme", newTheme);
  localStorage.setItem("theme", newTheme);
};

const toggleTheme = () => {
  const newTheme = theme.value === "light" ? "dark" : "light";
  applyTheme(newTheme);
};

onMounted(() => {
  // Check for saved theme preference or use system preference
  const savedTheme = localStorage.getItem("theme");
  const initialTheme = savedTheme || getSystemTheme();
  applyTheme(initialTheme);

  // Listen for system theme changes
  window
    .matchMedia("(prefers-color-scheme: dark)")
    .addEventListener("change", (e) => {
      if (!localStorage.getItem("theme")) {
        applyTheme(e.matches ? "dark" : "light");
      }
    });
});

// Personal information - Update these with your details
const personalInfo = {
  name: "Joseph Dodd",
  jobTitle: "Developer",
  bio: "A developer with experience in web development and cloud infrastructure, and a passion for new technologies and learning.",
  email: "hello@doddj.xyz",
  linkedin: "www.linkedin.com/in/joseph-dodd-a69b552bb",
  github: "https://github.com/Joseph-D1",
  imageUrl: "",
};

// Personal about section content
const personalAbout = ref(
  "Throughout my career, I have worked in many different roles. From a Restaurant Manager, a SCUBA diving instructor, to a Secondary School Teacher Aide, as well as a Web Developer. I believe that this variety of roles has helped me to develop many different skills, such as communication, collaboration, problem-solving, and time management."
);

// Professional about section content
const professionalAbout = ref(
  "I have experience in web development and cloud infrastructure, and I enjoy building infrastructure to host a variety of applications. I have a strong foundation in both frontend and backend technologies, with expertise in cloud platforms like AWS. I'm skilled in Infrastructure as Code (IaC), CI/CD pipelines, and containerization technologies."
);

const experiences = ref([
  {
    role: "Web Developer",
    company: "Pegasus Health",
    startDate: "April 2024",
    endDate: "August 2025",
    description:
      "Helped to implement new features, as well as transition the company site to a cloud-based solution.",
    achievements: [
      "Used IaC to deploy the company site to AWS.",
      "Implemented new features for the company site.",
      "Created a CI/CD pipeline to automate the deployment of the company site.",
    ],
  },
  // {
  //   role: "Previous Role",
  //   company: "Previous Company",
  //   startDate: "Jan 2018",
  //   endDate: "Dec 2019",
  //   description: "Description of your previous role and what you accomplished.",
  //   achievements: [
  //     "Significant achievement",
  //     "Project you worked on",
  //     "Skills you developed",
  //   ],
  // },
]);

const projects = ref([
  {
    title: "Website Infrastructure Transition",
    description:
      "Led a project to transition the company site to a cloud-based solution. Used Terraform to declare the infrastructure, and AWS Fargate to run managed Docker containers, which hosted the application. Ran a Redis Cache for session management, and AWS RDS to host the Database for the application.",
    technologies: ["Terraform", "AWS", "Nginx", "Docker"],
    liveUrl: "https://example.com",
    githubUrl: "https://github.com/example",
    imageUrl: "",
  },
  {
    title: "Managing Client Sites",
    description:
      "Managed the maintenence of client sites for over 50 Doctor's Offices, ensuring they were up to date and secure. Ran routine security scans to check for out of date plugins, or plugins with CVEs. Handled backups for clients, as well as meeting with clients to discuss changes and new requirements they had for their websites, such as new functionality or content updates.",
    technologies: ["WordPress", "Apache", "HTML", "CSS", "JavaScript"],
    liveUrl: "https://example.com",
    githubUrl: "",
    imageUrl: "",
  },
]);

const skillCategories = ref([
  {
    name: "Frontend",
    skills: [
      { name: "Vue.js", level: 90 },
      { name: "JavaScript", level: 85 },
      { name: "HTML/CSS", level: 95 },
      { name: "React", level: 75 },
    ],
  },
  {
    name: "Backend",
    skills: [
      { name: "PHP", level: 80 },
      { name: "Python", level: 75 },
      { name: "Node.js", level: 70 },
      { name: "SQL", level: 70 },
      { name: "Apache", level: 85 },
      { name: "Nginx", level: 80 },
    ],
  },
  {
    name: "Tools & Others",
    skills: [
      { name: "Git", level: 85 },
      { name: "Terraform", level: 85 },
      { name: "Docker", level: 70 },
      { name: "AWS", level: 70 },
    ],
  },
]);
</script>

<template>
  <div id="home">
    <Header
      :theme="theme"
      :name="personalInfo.name"
      :job-title="personalInfo.jobTitle"
      :tagline="personalInfo.bio"
      @toggle-theme="toggleTheme"
    />
    <main>
      <About
        :name="personalInfo.name"
        :job-title="personalInfo.jobTitle"
        :email="personalInfo.email"
        :linkedin="personalInfo.linkedin"
        :github="personalInfo.github"
        :image-url="personalInfo.imageUrl"
        :personal-about="personalAbout"
        :professional-about="professionalAbout"
      />
      <Experience :experiences="experiences" />
      <Projects :projects="projects" />
      <Skills :skill-categories="skillCategories" />
    </main>
    <Footer
      :name="personalInfo.name"
      :email="personalInfo.email"
      :linkedin="personalInfo.linkedin"
      :github="personalInfo.github"
    />
  </div>
</template>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

html {
  scroll-behavior: smooth;
}

body {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", "Roboto", "Oxygen",
    "Ubuntu", "Cantarell", "Fira Sans", "Droid Sans", "Helvetica Neue",
    sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
