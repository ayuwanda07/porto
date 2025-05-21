<template>
  <div class="app-container">
    <!-- Background with stars effect -->
    <div class="stars-container">
      <div class="stars"></div>
      <div class="stars2"></div>
      <div class="stars3"></div>
    </div>

    <!-- Navigation -->
    <header class="header">
      <div class="logo">AYU WANDA AZALIA</div>
      <nav class="nav">
        <ul>
          <li><a href="#home" @click.prevent="scrollToSection('home')">Home</a></li>
          <li><a href="#about" @click.prevent="scrollToSection('about')">About Me</a></li>
          <li><a href="#skills" @click.prevent="scrollToSection('skills')">Skills</a></li>
          <li><a href="#projects" @click.prevent="scrollToSection('projects')">Projects</a></li>
          <li><a href="#contact" @click.prevent="scrollToSection('contact')">Contact</a></li>
        </ul>
      </nav>
      <button class="mobile-nav-toggle" @click="toggleMobileNav">
        <span class="bar"></span>
        <span class="bar"></span>
        <span class="bar"></span>
      </button>
      <div class="mobile-nav" :class="{ 'active': mobileNavActive }">
        <ul>
          <li><a href="#home" @click="scrollToSection('home', true)">Home</a></li>
          <li><a href="#about" @click="scrollToSection('about', true)">About Me</a></li>
          <li><a href="#skills" @click="scrollToSection('skills', true)">Skills</a></li>
          <li><a href="#projects" @click="scrollToSection('projects', true)">Projects</a></li>
          <li><a href="#contact" @click="scrollToSection('contact', true)">Contact</a></li>
        </ul>
      </div>
    </header>

    <!-- Main Content -->
    <main>
      <!-- Home Section -->
      <section id="home" class="home-section">
        <div class="hero-content">
          <div class="hero-text">
            <h1 class="glitch-text" data-text="AYU WANDA AZALIA">AYU WANDA AZALIA</h1>
            <h2>Software Developer & QC Engineer</h2>
            <p>Building digital experiences that combine functionality with aesthetic excellence</p>
            <div class="hero-buttons">
              <button class="primary-btn" @click="scrollToSection('projects')">View Projects</button>
              <button class="secondary-btn" @click="scrollToSection('contact')">Contact Me</button>
            </div>
          </div>
          <div class="hero-image">
            <div class="profile-image-container">
              <div class="profile-image"></div>
              <div class="orbit">
                <div class="planet planet1"></div>
                <div class="planet planet2"></div>
                <div class="planet planet3"></div>
              </div>
            </div>
          </div>
        </div>
      </section>

      <!-- About Section -->
      <section id="about" class="about-section">
        <div class="section-header">
          <h2>About Me</h2>
          <div class="section-divider"></div>
        </div>
        <div class="about-content">
          <div class="about-text">
            <p>Informatics Engineering student with hands-on experience in full stack development, covering UI/UX design (Figma), front-end (Vue, Blade), back-end (Laravel), and deployment (VPS, Nginx).</p>
            <p>Certified Software Quality Control Tester (BNSP) with practical knowledge in test case design, defect tracking, and manual testing. Contributed to Agile-based projects used by 200+ users and rated 4.7+ on the Play Store.</p>
            <p>Passionate about delivering scalable, user-focused digital solutions with high functionality and quality.</p>
            
            <div class="education">
              <h3>Education</h3>
              <div class="education-item">
                <div class="year">2022 - Present</div>
                <div class="details">
                  <h4>Informatics Engineering (D4)</h4>
                  <p>Electronical Engineering Polytechnic Institute of Surabaya</p>
                  <p>GPA: 3.73 / 4.00; Current GPA: 3.59</p>
                </div>
              </div>
              <div class="education-item">
                <div class="year">2019 - 2022</div>
                <div class="details">
                  <h4>Science Major</h4>
                  <p>Barunawati High School, Surabaya</p>
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>

      <!-- Skills Section -->
      <section id="skills" class="skills-section">
        <div class="section-header">
          <h2>My Skills</h2>
          <div class="section-divider"></div>
        </div>
        <div class="skills-content">
          <div class="skill-category">
            <h3>UI/UX</h3>
            <div class="skills-grid">
              <div class="skill-item" v-for="(skill, index) in uiuxSkills" :key="'uiux-'+index">
                <div class="skill-icon">
                  <div class="skill-glow"></div>
                  <span>{{ skill }}</span>
                </div>
              </div>
            </div>
          </div>
          
          <div class="skill-category">
            <h3>Front-End</h3>
            <div class="skills-grid">
              <div class="skill-item" v-for="(skill, index) in frontendSkills" :key="'frontend-'+index">
                <div class="skill-icon">
                  <div class="skill-glow"></div>
                  <span>{{ skill }}</span>
                </div>
              </div>
            </div>
          </div>
          
          <div class="skill-category">
            <h3>Back-End & Database</h3>
            <div class="skills-grid">
              <div class="skill-item" v-for="(skill, index) in backendSkills" :key="'backend-'+index">
                <div class="skill-icon">
                  <div class="skill-glow"></div>
                  <span>{{ skill }}</span>
                </div>
              </div>
            </div>
          </div>
          
          <div class="skill-category">
            <h3>Other Skills</h3>
            <div class="skills-grid">
              <div class="skill-item" v-for="(skill, index) in otherSkills" :key="'other-'+index">
                <div class="skill-icon">
                  <div class="skill-glow"></div>
                  <span>{{ skill }}</span>
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>

      <!-- Projects Section -->
      <section id="projects" class="projects-section">
        <div class="section-header">
          <h2>My Projects</h2>
          <div class="section-divider"></div>
        </div>
        <div class="projects-grid">
          <div class="project-card" v-for="(project, index) in projects" :key="index" @click="openProjectDetails(index)">
            <div class="lightning-border">
              <span></span>
              <span></span>
              <span></span>
              <span></span>
            </div>
            <div class="project-image" :style="{ backgroundImage: `url(${project.image})` }">
              <div class="project-overlay">
                <h3>{{ project.title }}</h3>
                <p>{{ project.shortDescription }}</p>
                <button class="view-project-btn">View Details</button>
              </div>
            </div>
          </div>
        </div>
      </section>

      <!-- Contact Section -->
      <section id="contact" class="contact-section">
        <div class="section-header">
          <h2>Contact Me</h2>
          <div class="section-divider"></div>
        </div>
        <div class="contact-content">
          <div class="contact-info">
            <div class="contact-item">
              <div class="contact-icon">
                <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-mail"><rect width="20" height="16" x="2" y="4" rx="2"/><path d="m22 7-8.97 5.7a1.94 1.94 0 0 1-2.06 0L2 7"/></svg>
              </div>
              <div class="contact-text">
                <h3>Email</h3>
                <a href="mailto:wanda.azalia@gmail.com">wanda.azalia@gmail.com</a>
              </div>
            </div>
            <div class="contact-item">
              <div class="contact-icon">
                <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-linkedin"><path d="M16 8a6 6 0 0 1 6 6v7h-4v-7a2 2 0 0 0-2-2 2 2 0 0 0-2 2v7h-4v-7a6 6 0 0 1 6-6z"/><rect width="4" height="12" x="2" y="9"/><circle cx="4" cy="4" r="2"/></svg>
              </div>
              <div class="contact-text">
                <h3>LinkedIn</h3>
                <a href="https://linkedin.com/in/ayu-wanda-azalia/" target="_blank">linkedin.com/in/ayu-wanda-azalia/</a>
              </div>
            </div>
            <div class="contact-item">
              <div class="contact-icon">
                <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-github"><path d="M15 22v-4a4.8 4.8 0 0 0-1-3.5c3 0 6-2 6-5.5.08-1.25-.27-2.48-1-3.5.28-1.15.28-2.35 0-3.5 0 0-1 0-3 1.5-2.64-.5-5.36-.5-8 0C6 2 5 2 5 2c-.3 1.15-.3 2.35 0 3.5A5.403 5.403 0 0 0 4 9c0 3.5 3 5.5 6 5.5-.39.49-.68 1.05-.85 1.65-.17.6-.22 1.23-.15 1.85v4"/><path d="M9 18c-4.51 2-5-2-7-2"/></svg>
              </div>
              <div class="contact-text">
                <h3>GitHub</h3>
                <a href="https://github.com/ayuwanda07" target="_blank">github.com/ayuwanda07</a>
              </div>
            </div>
            
            <div class="contact-item">
              <div class="contact-icon">
                <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-map-pin"><path d="M20 10c0 6-8 12-8 12s-8-6-8-12a8 8 0 0 1 16 0Z"/><circle cx="12" cy="10" r="3"/></svg>
              </div>
              <div class="contact-text">
                <h3>Location</h3>
                <p>Surabaya, Jawa Timur</p>
              </div>
            </div>
          </div>
          <div class="contact-form">
            <h3>Send Me a Message</h3>
            <form @submit.prevent="submitForm">
              <div class="form-group">
                <label for="name">Name</label>
                <input type="text" id="name" v-model="contactForm.name" required>
              </div>
              <div class="form-group">
                <label for="email">Email</label>
                <input type="email" id="email" v-model="contactForm.email" required>
              </div>
              <div class="form-group">
                <label for="message">Message</label>
                <textarea id="message" v-model="contactForm.message" required></textarea>
              </div>
              <button type="submit" class="primary-btn">Send Message</button>
            </form>
          </div>
        </div>
      </section>
    </main>

    <!-- Footer -->
    <footer class="footer">
      <div class="footer-content">
        <p>&copy; {{ new Date().getFullYear() }} Ayu Wanda Azalia. All rights reserved.</p>
      </div>
    </footer>

    <!-- Project Details Modal -->
    <div class="project-modal" v-if="selectedProject !== null" @click.self="closeProjectDetails">
      <div class="project-modal-content">
        <button class="close-modal" @click="closeProjectDetails">&times;</button>
        <div class="project-details" v-if="selectedProject !== null">
          <h2>{{ projects[selectedProject].title }}</h2>
          <div class="project-details-content">
            <div class="project-details-images">
              <div class="image-slider">
                <button class="slider-nav prev" @click="prevImage">&lt;</button>
                <div class="slider-container">
                  <div class="slider-track" :style="{ transform: `translateX(-${currentSlide * 100}%)` }">
                    <div 
                      v-for="(img, idx) in projects[selectedProject].gallery" 
                      :key="idx" 
                      class="slider-slide"
                    >
                      <img :src="img" :alt="`${projects[selectedProject].title} image ${idx + 1}`">
                    </div>
                  </div>
                </div>
                <button class="slider-nav next" @click="nextImage">&gt;</button>
              </div>
              <div class="slider-dots">
                <span 
                  v-for="(img, idx) in projects[selectedProject].gallery" 
                  :key="idx" 
                  class="slider-dot" 
                  :class="{ active: currentSlide === idx }"
                  @click="goToSlide(idx)"
                ></span>
              </div>
            </div>
            <div class="project-details-info">
              <div class="project-details-section">
                <h3>Overview</h3>
                <p>{{ projects[selectedProject].description }}</p>
              </div>
              <div class="project-details-section">
                <h3>Role</h3>
                <p>{{ projects[selectedProject].role }}</p>
              </div>
              <div class="project-details-section">
                <h3>Technologies</h3>
                <div class="tech-tags">
                  <span v-for="(tech, idx) in projects[selectedProject].technologies" :key="idx" class="tech-tag">
                    {{ tech }}
                  </span>
                </div>
              </div>
              <div class="project-details-section">
                <h3>Duration</h3>
                <p>{{ projects[selectedProject].duration }}</p>
              </div>
              <div class="project-details-section" v-if="projects[selectedProject].links && projects[selectedProject].links.length > 0">
                <h3>Links</h3>
                <div class="project-links">
                  <a 
                    v-for="(link, idx) in projects[selectedProject].links" 
                    :key="idx" 
                    :href="link.url" 
                    target="_blank" 
                    class="project-link"
                  >
                    {{ link.text }}
                  </a>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      mobileNavActive: false,
      selectedProject: null,
      currentSlide: 0,
      contactForm: {
        name: '',
        email: '',
        message: ''
      },
      uiuxSkills: ['Figma', 'Prototyping', 'User Research', 'Wireframing', 'Visual Communication'],
      frontendSkills: ['HTML', 'CSS', 'JavaScript', 'Vue', 'React', 'Tailwind', 'TypeScript', 'Dart', 'Bootstrap'],
      backendSkills: ['PHP', 'Laravel', 'MySQL', 'PostgreSQL', 'SQLite'],
      otherSkills: ['Git', 'GitHub', 'Agile', 'Scrum', 'Kanban', 'Testing', 'Deployment', 'Nginx', 'VPS'],
      projects: [
        {
          title: 'Mealty App & Web',
          shortDescription: 'Healthy Food Recommendation Platform',
          description: 'A comprehensive platform that provides personalized healthy food recommendations based on user preferences and dietary requirements. The project includes both web and mobile applications with a focus on user experience and accessibility.',
          role: 'UI/UX Designer, Web Front-end & Scrum Master',
          technologies: ['ReactJS', 'TypeScript', 'Tailwind CSS', 'Flutter', 'Agile', 'Scrum'],
          duration: 'Jan 2024 - Dec 2024',
          image: '',
          gallery: [
            '/images/mealty/6.jpg',
            '/images/mealty/7.jpg',
            '/images/mealty/9.jpg',
            '/images/mealty/11.jpg'
          ],
          links: [
            { text: 'Website', url: 'https://mealty.agileteknik.com/' },
            { text: 'Playstore', url: 'https://play.google.com/store/apps/details?id=com.development.mealty&pcampaignid=web_share' }
          ]
        },
        {
          title: 'E-Commerce Software',
          shortDescription: 'Software Service Platform using AWS',
          description: 'A cloud-based e-commerce platform built on AWS infrastructure, providing scalable and reliable services for online businesses. The project focuses on real-time transactions, order processing, and efficient data management.',
          role: 'Web Front-End Developer & Database Management',
          technologies: ['Laravel', 'MySQL', 'AWS', 'Front-end Development'],
          duration: 'Feb - June 2024',
          image: '',
          gallery: [
            '/images/ecom/home.jpeg',
            '/images/ecom/home2.jpeg',
            '/images/ecom/home3.jpeg',
          ],
          links: [
            { text: 'Website', url: 'https://54.179.11.111' }
          ]
        },
        {
          title: 'Mobile Toefl App',
          shortDescription: 'TOEFL Learning Mobile App for PENS Student',
          description: 'A mobile application designed to help PENS students prepare for TOEFL examinations. The app provides practice tests, learning materials, and progress tracking to enhance the learning experience.',
          role: 'UI/UX Designer & Mobile Front-End Developer',
          technologies: ['Flutter', 'Figma', 'Mobile Development'],
          duration: 'April - May 2024',
          image: '',
          gallery: [
            '/images/toefl/toefl4.png',
            '/images/toefl/toefl5.png',
            '/images/toefl/toefl8.png',
            '/images/toefl/toefl6.png',
            '/images/toefl/toefl7.png'
          ],
          links: [
            { text : 'Figma' , url: 'https://www.figma.com/design/0peVeOxICLUDNBRScqeiY9/Test-Toefl-PENS?node-id=2-2&t=IdQjuxUDxh6SBT1s-1'}
          ]
        },
        {
          title: 'E-Commerce Platform BKN',
          shortDescription: 'Full Stack E-Commerce Website',
          description: 'A comprehensive e-commerce platform built during my internship at CV. Bintang Karya Nusantara. The project includes product listings, cart functionality, checkout process, and an admin panel for managing the store.',
          role: 'Full Stack Web Developer (Intern)',
          technologies: ['Laravel', 'Blade', 'Tailwind CSS', 'MySQL', 'RajaOngkir API', 'Linux VPS', 'Nginx'],
          duration: 'Jan 2025 - June 2025',
          image: '',
          gallery: [
            '/images/bkn/bkn1.png',
            '/images/bkn/bkn2.png',
            '/images/bkn/bkn3.png',
            '/images/bkn/bkn4.png'
          ],
          links: [
            { text : 'Website' , url: 'http://202.43.250.60:3000/'}
          ]
        }
      ]
    }
  },
  methods: {
    toggleMobileNav() {
      this.mobileNavActive = !this.mobileNavActive;
    },
    scrollToSection(sectionId, closeMobileNav = false) {
      const element = document.getElementById(sectionId);
      if (element) {
        window.scrollTo({
          top: element.offsetTop - 80,
          behavior: 'smooth'
        });
      }
      
      if (closeMobileNav) {
        this.mobileNavActive = false;
      }
    },
    openProjectDetails(index) {
      this.selectedProject = index;
      this.currentSlide = 0; // Reset slider to first image
      document.body.style.overflow = 'hidden';
    },
    closeProjectDetails() {
      this.selectedProject = null;
      document.body.style.overflow = 'auto';
    },
    prevImage() {
      if (this.selectedProject === null) return;
      const galleryLength = this.projects[this.selectedProject].gallery.length;
      this.currentSlide = (this.currentSlide - 1 + galleryLength) % galleryLength;
    },
    nextImage() {
      if (this.selectedProject === null) return;
      const galleryLength = this.projects[this.selectedProject].gallery.length;
      this.currentSlide = (this.currentSlide + 1) % galleryLength;
    },
    goToSlide(index) {
      this.currentSlide = index;
    },
    submitForm() {
      // In a real application, you would send this data to a server
      alert(`Thank you for your message, ${this.contactForm.name}! I'll get back to you soon.`);
      this.contactForm = {
        name: '',
        email: '',
        message: ''
      };
    }
  },
  mounted() {
    // Add scroll event listener to highlight active nav item
    window.addEventListener('scroll', () => {
      const sections = ['home', 'about', 'skills', 'projects', 'contact'];
      let current = '';
      
      sections.forEach(section => {
        const element = document.getElementById(section);
        if (element) {
          const rect = element.getBoundingClientRect();
          if (rect.top <= 100 && rect.bottom >= 100) {
            current = section;
          }
        }
      });
      
      // Update active nav item
      document.querySelectorAll('.nav ul li a').forEach(link => {
        link.classList.remove('active');
        if (link.getAttribute('href') === `#${current}`) {
          link.classList.add('active');
        }
      });
    });
  }
}
</script>

<style>
/* Override the default Vue styles that are limiting your layout */
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&display=swap');

#app {
  max-width: none !important;
  width: 100% !important;
  margin: 0 !important;
  padding: 0 !important;
  display: block !important;
}

body {
  display: block !important;
  place-items: unset !important;
  min-height: 100vh;
}

/* Keep all your existing custom styles from the portfolio */
/* Base Styles */
:root {
--primary-color: #6a3de8;
--secondary-color: #e83d84;
--accent-color: #3de8e8;
--dark-bg: #0a0a1a;
--darker-bg: #050510;
--light-text: #f0f0ff;
--muted-text: #a0a0c0;
--card-bg: rgba(20, 20, 40, 0.7);
--border-color: rgba(106, 61, 232, 0.3);
--glow-primary: rgba(106, 61, 232, 0.5);
--glow-secondary: rgba(232, 61, 132, 0.5);
--lightning-color1: #6a3de8;
--lightning-color2: #e83d84;
}

* {
margin: 0;
padding: 0;
box-sizing: border-box;
font-family: 'Poppins', sans-serif;
}

body {
background-color: var(--dark-bg);
color: var(--light-text);
line-height: 1.6;
overflow-x: hidden;
}

.app-container {
position: relative;
min-height: 100vh;
width: 100%;
overflow-x: hidden;
}

/* Stars Background */
.stars-container {
position: fixed;
top: 0;
left: 0;
width: 100%;
height: 100%;
z-index: -1;
background: linear-gradient(to bottom, var(--darker-bg), var(--dark-bg));
overflow: hidden;
}

.stars, .stars2, .stars3 {
position: absolute;
top: 0;
left: 0;
width: 100%;
height: 100%;
background: transparent;
}

.stars {
background-image: radial-gradient(2px 2px at 20px 30px, #ffffff, rgba(0, 0, 0, 0)),
                  radial-gradient(2px 2px at 40px 70px, #ffffff, rgba(0, 0, 0, 0)),
                  radial-gradient(2px 2px at 50px 160px, #ffffff, rgba(0, 0, 0, 0)),
                  radial-gradient(2px 2px at 90px 40px, #ffffff, rgba(0, 0, 0, 0)),
                  radial-gradient(2px 2px at 130px 80px, #ffffff, rgba(0, 0, 0, 0)),
                  radial-gradient(2px 2px at 160px 120px, #ffffff, rgba(0, 0, 0, 0));
background-repeat: repeat;
background-size: 200px 200px;
animation: animateStars 100s linear infinite;
opacity: 0.5;
}

.stars2 {
background-image: radial-gradient(1px 1px at 100px 50px, #ffffff, rgba(0, 0, 0, 0)),
                  radial-gradient(1px 1px at 200px 150px, #ffffff, rgba(0, 0, 0, 0)),
                  radial-gradient(1px 1px at 300px 200px, #ffffff, rgba(0, 0, 0, 0)),
                  radial-gradient(1px 1px at 400px 250px, #ffffff, rgba(0, 0, 0, 0)),
                  radial-gradient(1px 1px at 500px 300px, #ffffff, rgba(0, 0, 0, 0)),
                  radial-gradient(1px 1px at 50px 350px, #ffffff, rgba(0, 0, 0, 0));
background-repeat: repeat;
background-size: 300px 300px;
animation: animateStars 150s linear infinite;
opacity: 0.3;
}

.stars3 {
background-image: radial-gradient(1px 1px at 150px 150px, var(--accent-color), rgba(0, 0, 0, 0)),
                  radial-gradient(1px 1px at 250px 250px, var(--secondary-color), rgba(0, 0, 0, 0)),
                  radial-gradient(1px 1px at 350px 350px, var(--primary-color), rgba(0, 0, 0, 0));
background-repeat: repeat;
background-size: 400px 400px;
animation: animateStars 200s linear infinite;
opacity: 0.2;
}

@keyframes animateStars {
from {
  transform: translateY(0);
}
to {
  transform: translateY(-1000px);
}
}

/* Header & Navigation */
.header {
position: fixed;
top: 0;
left: 0;
width: 100%;
height: 80px;
display: flex;
align-items: center;
justify-content: space-between;
padding: 0 5%;
background: rgba(10, 10, 26, 0.8);
backdrop-filter: blur(10px);
z-index: 1000;
border-bottom: 1px solid var(--border-color);
}

.logo {
font-size: 1.5rem;
font-weight: 700;
color: var(--light-text);
letter-spacing: 1px;
background: linear-gradient(45deg, var(--primary-color), var(--secondary-color));
-webkit-background-clip: text;
-webkit-text-fill-color: transparent;
}

.nav ul {
display: flex;
list-style: none;
}

.nav ul li {
margin: 0 15px;
}

.nav ul li a {
color: var(--light-text);
text-decoration: none;
font-size: 1rem;
font-weight: 500;
transition: all 0.3s ease;
position: relative;
}

.nav ul li a::after {
content: '';
position: absolute;
bottom: -5px;
left: 0;
width: 0;
height: 2px;
background: linear-gradient(to right, var(--primary-color), var(--secondary-color));
transition: width 0.3s ease;
}

.nav ul li a:hover::after,
.nav ul li a.active::after {
width: 100%;
}

.mobile-nav-toggle {
display: none;
background: transparent;
border: none;
cursor: pointer;
}

.mobile-nav-toggle .bar {
display: block;
width: 25px;
height: 3px;
margin: 5px auto;
background-color: var(--light-text);
transition: all 0.3s ease;
}

.mobile-nav {
display: none;
}

/* Main Content Sections */
main {
padding-top: 80px;
width: 100%;
}

section {
padding: 100px 5%;
min-height: 100vh;
display: flex;
flex-direction: column;
justify-content: center;
width: 100%;
}

.section-header {
text-align: center;
margin-bottom: 50px;
}

.section-header h2 {
font-size: 2.5rem;
margin-bottom: 15px;
background: linear-gradient(45deg, var(--primary-color), var(--secondary-color));
-webkit-background-clip: text;
-webkit-text-fill-color: transparent;
}

.section-divider {
width: 80px;
height: 4px;
background: linear-gradient(to right, var(--primary-color), var(--secondary-color));
margin: 0 auto;
border-radius: 2px;
}

/* Home Section */
.home-section {
position: relative;
overflow: hidden;
width: 100%;
}

.hero-content {
display: flex;
align-items: center;
justify-content: space-between;
max-width: 1200px;
margin: 0 auto;
width: 100%;
}

.hero-text {
flex: 1;
padding-right: 50px;
}

.hero-text h1 {
font-size: 3.5rem;
font-weight: 700;
margin-bottom: 15px;
position: relative;
}

.glitch-text {
position: relative;
color: var(--light-text);
}

.glitch-text::before,
.glitch-text::after {
content: attr(data-text);
position: absolute;
top: 0;
left: 0;
width: 100%;
height: 100%;
}

.glitch-text::before {
left: 2px;
text-shadow: -2px 0 var(--primary-color);
clip: rect(44px, 450px, 56px, 0);
animation: glitch-anim 5s infinite linear alternate-reverse;
}

.glitch-text::after {
left: -2px;
text-shadow: -2px 0 var(--secondary-color);
clip: rect(44px, 450px, 56px, 0);
animation: glitch-anim2 5s infinite linear alternate-reverse;
}

@keyframes glitch-anim {
0% {
  clip: rect(42px, 9999px, 44px, 0);
}
5% {
  clip: rect(12px, 9999px, 59px, 0);
}
10% {
  clip: rect(48px, 9999px, 29px, 0);
}
15% {
  clip: rect(42px, 9999px, 73px, 0);
}
20% {
  clip: rect(63px, 9999px, 27px, 0);
}
25% {
  clip: rect(34px, 9999px, 55px, 0);
}
30% {
  clip: rect(86px, 9999px, 73px, 0);
}
35% {
  clip: rect(20px, 9999px, 20px, 0);
}
40% {
  clip: rect(26px, 9999px, 60px, 0);
}
45% {
  clip: rect(25px, 9999px, 66px, 0);
}
50% {
  clip: rect(57px, 9999px, 98px, 0);
}
55% {
  clip: rect(5px, 9999px, 46px, 0);
}
60% {
  clip: rect(82px, 9999px, 31px, 0);
}
65% {
  clip: rect(54px, 9999px, 27px, 0);
}
70% {
  clip: rect(28px, 9999px, 99px, 0);
}
75% {
  clip: rect(45px, 9999px, 69px, 0);
}
80% {
  clip: rect(23px, 9999px, 85px, 0);
}
85% {
  clip: rect(54px, 9999px, 84px, 0);
}
90% {
  clip: rect(45px, 9999px, 47px, 0);
}
95% {
  clip: rect(37px, 9999px, 20px, 0);
}
100% {
  clip: rect(4px, 9999px, 91px, 0);
}
}

@keyframes glitch-anim2 {
0% {
  clip: rect(65px, 9999px, 100px, 0);
}
5% {
  clip: rect(52px, 9999px, 74px, 0);
}
10% {
  clip: rect(79px, 9999px, 85px, 0);
}
15% {
  clip: rect(75px, 9999px, 5px, 0);
}
20% {
  clip: rect(67px, 9999px, 61px, 0);
}
25% {
  clip: rect(14px, 9999px, 79px, 0);
}
30% {
  clip: rect(1px, 9999px, 66px, 0);
}
35% {
  clip: rect(86px, 9999px, 30px, 0);
}
40% {
  clip: rect(23px, 9999px, 98px, 0);
}
45% {
  clip: rect(85px, 9999px, 72px, 0);
}
50% {
  clip: rect(71px, 9999px, 75px, 0);
}
55% {
  clip: rect(2px, 9999px, 48px, 0);
}
60% {
  clip: rect(30px, 9999px, 16px, 0);
}
65% {
  clip: rect(59px, 9999px, 50px, 0);
}
70% {
  clip: rect(41px, 9999px, 62px, 0);
}
75% {
  clip: rect(2px, 9999px, 82px, 0);
}
80% {
  clip: rect(47px, 9999px, 73px, 0);
}
85% {
  clip: rect(3px, 9999px, 27px, 0);
}
90% {
  clip: rect(26px, 9999px, 55px, 0);
}
95% {
  clip: rect(42px, 9999px, 97px, 0);
}
100% {
  clip: rect(38px, 9999px, 49px, 0);
}
}

.hero-text h2 {
font-size: 1.8rem;
font-weight: 500;
margin-bottom: 20px;
color: var(--accent-color);
}

.hero-text p {
font-size: 1.2rem;
margin-bottom: 30px;
color: var(--muted-text);
}

.hero-buttons {
display: flex;
gap: 20px;
}

.primary-btn, .secondary-btn {
padding: 12px 30px;
border-radius: 50px;
font-size: 1rem;
font-weight: 500;
cursor: pointer;
transition: all 0.3s ease;
border: none;
outline: none;
}

.primary-btn {
background: linear-gradient(45deg, var(--primary-color), var(--secondary-color));
color: var(--light-text);
box-shadow: 0 5px 15px rgba(106, 61, 232, 0.3);
}

.primary-btn:hover {
transform: translateY(-3px);
box-shadow: 0 8px 20px rgba(106, 61, 232, 0.5);
}

.secondary-btn {
background: transparent;
color: var(--light-text);
border: 2px solid var(--primary-color);
}

.secondary-btn:hover {
background: rgba(106, 61, 232, 0.1);
transform: translateY(-3px);
}

.hero-image {
flex: 1;
display: flex;
justify-content: center;
align-items: center;
}

.profile-image-container {
position: relative;
width: 300px;
height: 300px;
}

.profile-image {
width: 100%;
height: 100%;
border-radius: 50%;
background: linear-gradient(45deg, var(--primary-color), var(--secondary-color));
position: relative;
overflow: hidden;
box-shadow: 0 0 30px var(--glow-primary);
}

.profile-image::before {
content: '';
position: absolute;
top: 10px;
left: 10px;
right: 10px;
bottom: 10px;
background: url('https://via.placeholder.com/280x280/1a1a2e/ffffff?text=AW') center/cover;
border-radius: 50%;
}

.orbit {
position: absolute;
top: -50px;
left: -50px;
width: 400px;
height: 400px;
border: 1px dashed rgba(255, 255, 255, 0.2);
border-radius: 50%;
animation: rotate 20s linear infinite;
}

.planet {
position: absolute;
width: 30px;
height: 30px;
border-radius: 50%;
box-shadow: 0 0 10px rgba(255, 255, 255, 0.5);
}

.planet1 {
background: var(--primary-color);
top: 50px;
left: 185px;
}

.planet2 {
background: var(--secondary-color);
top: 185px;
right: 50px;
}

.planet3 {
background: var(--accent-color);
bottom: 50px;
left: 185px;
}

@keyframes rotate {
from {
  transform: rotate(0deg);
}
to {
  transform: rotate(360deg);
}
}

/* About Section */
.about-content {
display: flex;
flex-direction: column;
max-width: 900px;
margin: 0 auto;
width: 100%;
}

.about-text {
margin-bottom: 40px;
}

.about-text p {
margin-bottom: 20px;
font-size: 1.1rem;
}

.education {
margin-top: 30px;
}

.education h3 {
font-size: 1.5rem;
margin-bottom: 20px;
color: var(--accent-color);
}

.education-item {
display: flex;
margin-bottom: 30px;
position: relative;
padding-left: 30px;
}

.education-item::before {
content: '';
position: absolute;
left: 0;
top: 8px;
width: 12px;
height: 12px;
border-radius: 50%;
background: var(--primary-color);
box-shadow: 0 0 10px var(--glow-primary);
}

.education-item::after {
content: '';
position: absolute;
left: 5px;
top: 25px;
width: 2px;
height: calc(100% - 20px);
background: linear-gradient(to bottom, var(--primary-color), transparent);
}

.education-item:last-child::after {
display: none;
}

.year {
min-width: 150px;
font-weight: 600;
color: var(--secondary-color);
}

.details h4 {
font-size: 1.2rem;
margin-bottom: 5px;
}

.details p {
color: var(--muted-text);
margin-bottom: 5px;
}

/* Skills Section */
.skills-content {
max-width: 1000px;
margin: 0 auto;
width: 100%;
}

.skill-category {
margin-bottom: 40px;
}

.skill-category h3 {
font-size: 1.5rem;
margin-bottom: 20px;
color: var(--accent-color);
text-align: center;
}

.skills-grid {
display: grid;
grid-template-columns: repeat(auto-fill, minmax(150px, 1fr));
gap: 20px;
}

.skill-item {
display: flex;
justify-content: center;
}

.skill-icon {
position: relative;
width: 120px;
height: 120px;
display: flex;
align-items: center;
justify-content: center;
border-radius: 50%;
background: var(--card-bg);
border: 1px solid var(--border-color);
transition: all 0.3s ease;
overflow: hidden;
}

.skill-icon:hover {
transform: translateY(-5px);
box-shadow: 0 10px 20px rgba(0, 0, 0, 0.3);
}

.skill-icon span {
z-index: 2;
font-weight: 500;
text-align: center;
}

.skill-glow {
position: absolute;
top: 50%;
left: 50%;
transform: translate(-50%, -50%);
width: 0;
height: 0;
background: radial-gradient(circle, var(--glow-primary), transparent 70%);
border-radius: 50%;
opacity: 0.5;
transition: all 0.5s ease;
}

.skill-icon:hover .skill-glow {
width: 150px;
height: 150px;
}

/* Projects Section */
.projects-grid {
display: grid;
grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
gap: 30px;
max-width: 1200px;
margin: 0 auto;
width: 100%;
}

.project-card {
position: relative;
height: 250px;
border-radius: 10px;
overflow: hidden;
cursor: pointer;
transition: all 0.3s ease;
box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
width: 100%;
min-width: 250px;
}

/* Lightning Border Animation */
.lightning-border {
position: absolute;
top: 0;
left: 0;
width: 100%;
height: 100%;
z-index: 2;
pointer-events: none;
}

.lightning-border span {
position: absolute;
display: block;
}

.lightning-border span:nth-child(1) {
top: 0;
left: 0;
width: 100%;
height: 2px;
background: linear-gradient(90deg, transparent, var(--lightning-color1));
animation: lightning1 1.5s linear infinite;
}

.lightning-border span:nth-child(2) {
top: 0;
right: 0;
width: 2px;
height: 100%;
background: linear-gradient(180deg, transparent, var(--lightning-color2));
animation: lightning2 1.5s linear infinite;
animation-delay: 0.375s;
}

.lightning-border span:nth-child(3) {
bottom: 0;
right: 0;
width: 100%;
height: 2px;
background: linear-gradient(270deg, transparent, var(--lightning-color1));
animation: lightning3 1.5s linear infinite;
animation-delay: 0.75s;
}

.lightning-border span:nth-child(4) {
bottom: 0;
left: 0;
width: 2px;
height: 100%;
background: linear-gradient(360deg, transparent, var(--lightning-color2));
animation: lightning4 1.5s linear infinite;
animation-delay: 1.125s;
}

@keyframes lightning1 {
0% {
  left: -100%;
}
50%, 100% {
  left: 100%;
}
}

@keyframes lightning2 {
0% {
  top: -100%;
}
50%, 100% {
  top: 100%;
}
}

@keyframes lightning3 {
0% {
  right: -100%;
}
50%, 100% {
  right: 100%;
}
}

@keyframes lightning4 {
0% {
  bottom: -100%;
}
50%, 100% {
  bottom: 100%;
}
}

.project-image {
width: 100%;
height: 100%;
background-size: cover;
background-position: center;
transition: all 0.5s ease;
}

.project-card:hover .project-image {
transform: scale(1.1);
}

.project-overlay {
position: absolute;
top: 0;
left: 0;
width: 100%;
height: 100%;
background: linear-gradient(to top, rgba(10, 10, 26, 0.9), rgba(10, 10, 26, 0.5));
display: flex;
flex-direction: column;
justify-content: flex-end;
padding: 20px;
opacity: 1; /* Always visible */
transition: all 0.3s ease;
}

.project-overlay h3 {
font-size: 1.5rem;
margin-bottom: 10px;
}

.project-overlay p {
font-size: 0.9rem;
color: var(--muted-text);
margin-bottom: 15px;
}

.view-project-btn {
align-self: flex-start;
padding: 8px 20px;
background: linear-gradient(45deg, var(--primary-color), var(--secondary-color));
color: var(--light-text);
border: none;
border-radius: 50px;
font-size: 0.9rem;
cursor: pointer;
transition: all 0.3s ease;
}

.view-project-btn:hover {
transform: scale(1.05);
box-shadow: 0 5px 15px rgba(106, 61, 232, 0.3);
}

/* Project Modal */
.project-modal {
position: fixed;
top: 0;
left: 0;
width: 100%;
height: 100%;
background: rgba(5, 5, 16, 0.9);
backdrop-filter: blur(5px);
z-index: 2000;
display: flex;
align-items: center;
justify-content: center;
padding: 20px;
overflow-y: auto;
}

.project-modal-content {
background: var(--card-bg);
border-radius: 10px;
width: 90%;
max-width: 1000px;
max-height: 90vh;
overflow-y: auto;
position: relative;
border: 1px solid var(--border-color);
box-shadow: 0 0 30px rgba(106, 61, 232, 0.2);
}

.close-modal {
position: absolute;
top: 20px;
right: 20px;
background: transparent;
border: none;
color: var(--light-text);
font-size: 2rem;
cursor: pointer;
z-index: 10;
}

.project-details {
padding: 30px;
}

.project-details h2 {
font-size: 2rem;
margin-bottom: 30px;
text-align: center;
background: linear-gradient(45deg, var(--primary-color), var(--secondary-color));
-webkit-background-clip: text;
-webkit-text-fill-color: transparent;
}

.project-details-content {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 30px;
}

/* Image Slider */
.project-details-images {
display: flex;
flex-direction: column;
gap: 15px;
}

.image-slider {
position: relative;
width: 100%;
height: 300px;
border-radius: 10px;
overflow: hidden;
box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
display: flex;
align-items: center;
}

.slider-container {
width: 100%;
height: 100%;
overflow: hidden;
}

.slider-track {
display: flex;
width: 100%;
height: 100%;
transition: transform 0.5s ease;
}

.slider-slide {
min-width: 100%;
height: 100%;
display: flex;
align-items: center;
justify-content: center;
}

.slider-slide img {
width: 100%;
height: 100%;
object-fit: cover;
}

.slider-nav {
position: absolute;
top: 50%;
transform: translateY(-50%);
width: 40px;
height: 40px;
background: rgba(10, 10, 26, 0.7);
border: none;
border-radius: 50%;
color: var(--light-text);
font-size: 1.5rem;
display: flex;
align-items: center;
justify-content: center;
cursor: pointer;
z-index: 10;
transition: all 0.3s ease;
}

.slider-nav:hover {
background: var(--primary-color);
}

.slider-nav.prev {
left: 10px;
}

.slider-nav.next {
right: 10px;
}

.slider-dots {
display: flex;
justify-content: center;
gap: 10px;
margin-top: 15px;
}

.slider-dot {
width: 12px;
height: 12px;
border-radius: 50%;
background: rgba(255, 255, 255, 0.3);
cursor: pointer;
transition: all 0.3s ease;
}

.slider-dot.active {
background: var(--primary-color);
transform: scale(1.2);
}

.slider-dot:hover {
background: var(--secondary-color);
}

.project-details-info {
display: flex;
flex-direction: column;
gap: 20px;
}

.project-details-section h3 {
font-size: 1.3rem;
margin-bottom: 10px;
color: var(--accent-color);
}

.project-details-section p {
color: var(--muted-text);
line-height: 1.6;
}

.tech-tags {
display: flex;
flex-wrap: wrap;
gap: 10px;
}

.tech-tag {
padding: 5px 15px;
background: rgba(106, 61, 232, 0.2);
border-radius: 50px;
font-size: 0.9rem;
color: var(--light-text);
border: 1px solid var(--border-color);
}

.project-links {
display: flex;
gap: 15px;
}

.project-link {
padding: 8px 20px;
background: linear-gradient(45deg, var(--primary-color), var(--secondary-color));
color: var(--light-text);
text-decoration: none;
border-radius: 50px;
font-size: 0.9rem;
transition: all 0.3s ease;
}

.project-link:hover {
transform: translateY(-3px);
box-shadow: 0 5px 15px rgba(106, 61, 232, 0.3);
}

/* Contact Section */
.contact-content {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 50px;
max-width: 1000px;
margin: 0 auto;
width: 100%;
}

.contact-info {
display: flex;
flex-direction: column;
gap: 30px;
}

.contact-item {
display: flex;
align-items: flex-start;
gap: 15px;
}

.contact-icon {
width: 50px;
height: 50px;
background: var(--card-bg);
border-radius: 50%;
display: flex;
align-items: center;
justify-content: center;
border: 1px solid var(--border-color);
color: var(--primary-color);
}

.contact-text h3 {
font-size: 1.2rem;
margin-bottom: 5px;
}

.contact-text a, .contact-text p {
color: var(--muted-text);
text-decoration: none;
transition: all 0.3s ease;
}

.contact-text a:hover {
color: var(--primary-color);
}

.contact-form {
background: var(--card-bg);
padding: 30px;
border-radius: 10px;
border: 1px solid var(--border-color);
}

.contact-form h3 {
font-size: 1.5rem;
margin-bottom: 20px;
text-align: center;
color: var(--accent-color);
}

.form-group {
margin-bottom: 20px;
}

.form-group label {
display: block;
margin-bottom: 8px;
font-weight: 500;
}

.form-group input, .form-group textarea {
width: 100%;
padding: 12px 15px;
background: rgba(255, 255, 255, 0.05);
border: 1px solid var(--border-color);
border-radius: 5px;
color: var(--light-text);
font-size: 1rem;
transition: all 0.3s ease;
}

.form-group textarea {
height: 150px;
resize: vertical;
}

.form-group input:focus, .form-group textarea:focus {
outline: none;
border-color: var(--primary-color);
box-shadow: 0 0 10px rgba(106, 61, 232, 0.2);
}

/* Footer */
.footer {
background: var(--darker-bg);
padding: 30px 5%;
border-top: 1px solid var(--border-color);
width: 100%;
}

.footer-content {
max-width: 1200px;
margin: 0 auto;
text-align: center;
}

.footer-content p {
color: var(--muted-text);
font-size: 0.9rem;
}

/* Responsive Styles */
@media (max-width: 992px) {
.hero-content {
  flex-direction: column;
  text-align: center;
}

.hero-text {
  padding-right: 0;
  margin-bottom: 50px;
}

.hero-buttons {
  justify-content: center;
}

.project-details-content {
  grid-template-columns: 1fr;
}

.contact-content {
  grid-template-columns: 1fr;
}
}

@media (max-width: 768px) {
.nav {
  display: none;
}

.mobile-nav-toggle {
  display: block;
}

.mobile-nav.active {
  display: block;
  position: fixed;
  top: 80px;
  left: 0;
  width: 100%;
  background: var(--dark-bg);
  padding: 20px;
  border-bottom: 1px solid var(--border-color);
}

.mobile-nav ul {
  list-style: none;
}

.mobile-nav ul li {
  margin: 15px 0;
}

.mobile-nav ul li a {
  color: var(--light-text);
  text-decoration: none;
  font-size: 1.2rem;
  display: block;
  padding: 10px;
  border-radius: 5px;
  transition: all 0.3s ease;
}

.mobile-nav ul li a:hover {
  background: rgba(106, 61, 232, 0.1);
}

.mobile-nav-toggle.active .bar:nth-child(1) {
  transform: translateY(8px) rotate(45deg);
}

.mobile-nav-toggle.active .bar:nth-child(2) {
  opacity: 0;
}

.mobile-nav-toggle.active .bar:nth-child(3) {
  transform: translateY(-8px) rotate(-45deg);
}

.skills-grid {
  grid-template-columns: repeat(auto-fill, minmax(120px, 1fr));
}

.projects-grid {
  grid-template-columns: 1fr;
  padding: 0 15px;
}

.project-card {
  height: 220px;
  margin-bottom: 20px;
}
}

@media (max-width: 576px) {
.hero-text h1 {
  font-size: 2.5rem;
}

.hero-text h2 {
  font-size: 1.5rem;
}

.section-header h2 {
  font-size: 2rem;
}

.hero-buttons {
  flex-direction: column;
  gap: 15px;
}

.primary-btn, .secondary-btn {
  width: 100%;
}

.skills-grid {
  grid-template-columns: repeat(2, 1fr);
}

.education-item {
  flex-direction: column;
}

.year {
  margin-bottom: 10px;
}

.image-slider {
  height: 200px;
}

.projects-grid {
  grid-template-columns: 1fr;
  gap: 20px;
}

.project-card {
  height: 200px;
}

.project-overlay h3 {
  font-size: 1.3rem;
}

.project-overlay p {
  font-size: 0.85rem;
}

.view-project-btn {
  padding: 6px 15px;
  font-size: 0.8rem;
}
}
</style>