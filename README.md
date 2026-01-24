# Portfolio Website

A modern, responsive portfolio website built with Vue 3 and Vite. Features a clean design with dark/light theme support, smooth animations, and a mobile-friendly interface.

## 🚀 Features

- **Modern Design**: Clean, professional layout with smooth animations
- **Dark/Light Theme**: Automatic theme detection with manual toggle option
- **Responsive**: Fully responsive design that works on all devices
- **Fast Performance**: Built with Vite for optimal performance
- **SEO Friendly**: Semantic HTML structure
- **Smooth Scrolling**: Enhanced navigation experience

## 📋 Table of Contents

- [Project Structure](#project-structure)
- [Getting Started](#getting-started)
- [Updating Information](#updating-information)
- [Component Guide](#component-guide)
- [Customization](#customization)
- [Building for Production](#building-for-production)
- [Hosting](#hosting)
- [Technologies Used](#technologies-used)

## 📁 Project Structure

```
portfolio/
├── public/                 # Static assets (favicons, etc.)
├── src/
│   ├── assets/            # Images and other assets
│   │   └── images/        # Profile and project images
│   ├── components/        # Vue components
│   │   ├── About.vue      # About section component
│   │   ├── Experience.vue # Work experience timeline
│   │   ├── Footer.vue     # Footer with contact links
│   │   ├── Header.vue     # Navigation and hero section
│   │   ├── Projects.vue   # Projects showcase
│   │   └── Skills.vue     # Skills with progress bars
│   ├── App.vue            # Main application component
│   ├── main.js            # Application entry point
│   └── style.css          # Global styles and CSS variables
├── index.html             # HTML template
├── package.json           # Dependencies and scripts
├── vite.config.js        # Vite configuration
└── README.md             # This file
```

## 🛠️ Getting Started

### Prerequisites

- Node.js (v16 or higher recommended)
- npm or yarn

### Installation

1. Clone the repository:

```bash
git clone https://github.com/Joseph-D1/personal-site.git
cd portfolio
```

2. Install dependencies:

```bash
npm install
```

3. Start the development server:

```bash
npm run dev
```

4. Open your browser and navigate to `http://localhost:5173`

## 📝 Updating Information

All personal information is stored in `src/App.vue`. You can update the following:

### Personal Information

Located in the `personalInfo` object (lines 51-59):

```javascript
const personalInfo = {
  name: "Joseph Dodd", // Your full name
  jobTitle: "Developer", // Your job title
  bio: "A developer with...", // Short bio/tagline
  email: "hello@doddj.xyz", // Your email
  linkedin: "www.linkedin.com/in/...", // LinkedIn profile URL
  github: "https://github.com/...", // GitHub profile URL
  imageUrl: "", // Profile image URL (optional)
};
```

### About Section Content

Update the `personalAbout` and `professionalAbout` refs (lines 62-69):

```javascript
const personalAbout = ref("Your personal story and background...");

const professionalAbout = ref("Your professional experience and expertise...");
```

### Work Experience

Update the `experiences` array (lines 71-97). Each experience object should have:

```javascript
{
  role: "Web Developer",                    // Job title
  company: "Pegasus Health",                // Company name
  startDate: "April 2024",                  // Start date
  endDate: "August 2025",                   // End date (or "Present")
  description: "Brief description...",     // Job description
  achievements: [                           // List of achievements
    "Achievement 1",
    "Achievement 2",
    "Achievement 3"
  ]
}
```

### Projects

Update the `projects` array (lines 99-118). Each project should include:

```javascript
{
  title: "Project Title",                   // Project name
  description: "Project description...",    // What the project does
  technologies: ["Vue.js", "AWS"],         // Technologies used
  liveUrl: "https://example.com",          // Live demo URL (optional)
  githubUrl: "https://github.com/...",     // GitHub repo URL (optional)
  imageUrl: "",                            // Project image URL (optional)
}
```

### Skills

Update the `skillCategories` array (lines 120-150). Skills are organized by category:

```javascript
{
  name: "Frontend",                         // Category name
  skills: [
    { name: "Vue.js", level: 90 },        // Skill name and proficiency (0-100)
    { name: "JavaScript", level: 85 }
  ]
}
```

## 🧩 Component Guide

### Header Component (`src/components/Header.vue`)

**Purpose**: Navigation bar and hero section with profile image.

**Props**:

- `theme` (String): Current theme ("light" or "dark")
- `name` (String): Your name
- `jobTitle` (String): Your job title
- `tagline` (String): Short bio/tagline

**Customization**:

- **Profile Image**: The component imports `joeFlorence.jpeg` from `src/assets/images/`. To change it:
  1. Replace the image file in `src/assets/images/`
  2. Update the import on line 126: `import profileImage from "@/assets/images/your-image.jpg"`
- **Navigation Links**: Modify the navigation items in the template (lines 7-19)
- **Hero Buttons**: Customize the call-to-action buttons (lines 99-112)

### About Component (`src/components/About.vue`)

**Purpose**: Displays personal and professional information with contact details.

**Props**:

- `name` (String): Your name
- `jobTitle` (String): Your job title
- `email` (String): Email address
- `linkedin` (String): LinkedIn URL
- `github` (String): GitHub URL
- `imageUrl` (String): Optional profile image
- `personalAbout` (String): Personal story text
- `professionalAbout` (String): Professional background text

**Customization**:

- **Section Title**: Change "Who am I?" on line 4
- **Card Icons**: Modify emoji icons (lines 7, 14)
- **Card Titles**: Update the card headings (lines 9, 16)
- **Layout**: Adjust grid layout in the styles section

### Experience Component (`src/components/Experience.vue`)

**Purpose**: Timeline display of work experience.

**Props**:

- `experiences` (Array): Array of experience objects

**Customization**:

- **Section Title**: Change "Experience" on line 4
- **Timeline Styling**: Modify colors and spacing in the styles section
- **Date Format**: Adjust how dates are displayed (line 15)

### Projects Component (`src/components/Projects.vue`)

**Purpose**: Showcase of your projects in a card grid layout.

**Props**:

- `projects` (Array): Array of project objects

**Customization**:

- **Section Title**: Change "Projects" on line 4
- **Grid Layout**: Adjust `grid-template-columns` in styles (line 112)
- **Card Styling**: Modify colors, shadows, and hover effects
- **Tech Tags**: Customize the technology tag appearance (lines 171-178)

### Skills Component (`src/components/Skills.vue`)

**Purpose**: Display skills organized by category with progress bars.

**Props**:

- `skillCategories` (Array): Array of skill category objects

**Customization**:

- **Section Title**: Change "Skills" on line 4
- **Progress Bar Colors**: Modify gradient in styles (line 164)
- **Category Layout**: Adjust grid layout (line 104)
- **Animation**: Customize the progress bar animation (lines 170-174)

### Footer Component (`src/components/Footer.vue`)

**Purpose**: Footer with copyright and social links.

**Props**:

- `name` (String): Your name
- `email` (String): Email address
- `linkedin` (String): LinkedIn URL
- `github` (String): GitHub URL
- `twitter` (String): Optional Twitter URL

**Customization**:

- **Copyright Text**: Modify the footer text (line 5)
- **Social Links**: Add or remove social media links (lines 6-23)

## 🎨 Customization

### Colors and Themes

All color variables are defined in `src/style.css` (lines 1-38). You can customize:

**Light Mode Colors** (lines 1-10):

```css
--primary-color: #4aa7ff; /* Main brand color */
--secondary-color: #1a28f3; /* Secondary accent */
--text-color: #1f2937; /* Main text color */
--text-secondary: #6b7280; /* Secondary text */
--bg-color: #ffffff; /* Background */
--section-bg: #f9fafb; /* Section backgrounds */
```

**Dark Mode Colors** (lines 28-38):

```css
[data-theme="dark"] {
  --primary-color: #8191f8;
  --secondary-color: #8bb2fa;
  /* ... */
}
```

### Typography

Font settings are in `src/style.css`. The default uses system fonts for optimal performance.

### Images

1. **Profile Image**: Place in `src/assets/images/` and update the import in `Header.vue`
2. **Project Images**: Add to `src/assets/images/` and reference in project objects
3. **Favicon**: Replace files in `public/` directory

## 🏗️ Building for Production

1. Build the project:

```bash
npm run build
```

2. Preview the production build:

```bash
npm run preview
```

The built files will be in the `dist/` directory, ready for deployment.

## 🌐 Hosting

### Hosting Platform

**[TODO: Add your hosting information]**

**Current Hosting**:

Currently hosted on Vercel

**Domain**: [find it here](https://personal-site-wheat-pi-73.vercel.app/)

**Deployment Method**:

Automatic deployment after a successful merge onto main

### Deployment Steps

1. Push your code to GitHub
2. Import the repository in Vercel
3. Configure build settings:
   - Build Command: `npm run build`
   - Output Directory: `dist`
4. Deploy

### Environment Variables

**[TODO: Add if you use environment variables]**

If you need environment variables, create a `.env` file:

```
VITE_API_URL=your-api-url
VITE_ANALYTICS_ID=your-analytics-id
```

Access them in code with: `import.meta.env.VITE_API_URL`

### Custom Domain Setup

**[TODO: Add domain configuration steps if applicable]**

1. Purchase/configure domain
2. Update DNS records
3. Configure SSL certificate
4. Update any hardcoded URLs in the code

## 📦 Technologies Used

- **Vue 3**: Progressive JavaScript framework
- **Vite**: Next-generation frontend tooling
- **CSS3**: Modern styling with CSS variables
- **JavaScript (ES6+)**: Modern JavaScript features

## 📄 License

[Add your license information here]

## 👤 Author

**Joseph Dodd**

- Email: jreiddodd@gmail.com
- LinkedIn: [Your LinkedIn Profile]
- GitHub: [@Joseph-D1](https://github.com/Joseph-D1)

---

## 🔧 Troubleshooting

### Common Issues

**Build fails:**

- Ensure Node.js version is 16+
- Delete `node_modules` and `package-lock.json`, then run `npm install` again

**Images not loading:**

- Check file paths are correct
- Ensure images are in `src/assets/images/` directory
- Use relative paths or the `@/` alias

**Theme not persisting:**

- Check browser localStorage is enabled
- Clear browser cache and try again

**Styles not applying:**

- Ensure `style.css` is imported in `main.js`
- Check CSS variable names match in all components

---

**Need help?** Open an issue or contact the author.
