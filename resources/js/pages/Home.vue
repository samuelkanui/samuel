<script setup lang="ts">
import { ref, onMounted } from 'vue';
import { Head, Link } from '@inertiajs/vue3';
import PortfolioLayout from '@/layouts/PortfolioLayout.vue';
import { ArrowRight, Download, Github, ExternalLink, Code, Zap } from 'lucide-vue-next';

// Skills organized by category for software engineer
const skillCategories = [
  {
    title: '🧩 Programming & Frameworks',
    skills: ['PHP (Laravel)', 'JavaScript (React/Vue)', 'Dart (Flutter)', 'HTML5/CSS3', 'TypeScript', 'Python']
  },
  {
    title: '🔐 Cybersecurity & Networking', 
    skills: ['Cisco Networking (CCNA 1-3)', 'Encryption (AES, RSA, SSL/TLS)', 'Secure Coding', 'Vulnerability Assessment']
  },
  {
    title: '⚙️ Tools & Platforms',
    skills: ['Git/GitHub', 'Docker', 'MySQL/PostgreSQL', 'AWS/DigitalOcean', 'Postman', 'Linux']
  },
  {
    title: '🧪 Development Practices',
    skills: ['RESTful APIs', 'Unit Testing (PHPUnit)', 'Agile/Scrum', 'CI/CD (GitHub Actions)']
  }
];

const certifications = [
  {
    title: 'Cisco Networking (CCNA 1)',
    issuer: 'Cisco Systems',
    year: '2024',
    verified: true
  },
  {
    title: 'Cisco Networking (CCNA 2)', 
    issuer: 'Cisco Systems',
    year: '2024',
    verified: true
  },
  {
    title: 'Cisco Networking (CCNA 3)',
    issuer: 'Cisco Systems', 
    year: '2024',
    verified: true
  },
  {
    title: 'Encryption & Cybersecurity Fundamentals',
    issuer: 'Security Institute',
    year: '2023',
    verified: true
  }
];

const featuredProjects = [
  {
    title: 'Secure Banking Mobile App',
    description: 'Cross-platform mobile banking application with biometric authentication and AES-256 encryption',
    image: '/images/project1.jpg',
    tech: ['Flutter', 'Laravel API', 'JWT Auth', 'AES Encryption'],
    features: [
      'Biometric authentication (fingerprint/face)',
      'End-to-end encryption for transactions', 
      'Real-time fraud detection',
      'Offline transaction queuing'
    ],
    github: 'https://github.com/username/secure-banking-app',
    demo: 'https://demo-banking.com',
    category: 'mobile'
  },
  {
    title: 'Network Security Dashboard',
    description: 'Real-time network monitoring system with threat detection and automated response capabilities',
    image: '/images/project2.jpg', 
    tech: ['Laravel', 'Vue.js', 'WebSocket', 'Cisco APIs'],
    features: [
      'Real-time network traffic analysis',
      'Automated threat detection algorithms',
      'Integration with Cisco network devices',
      'Custom security alert system'
    ],
    github: 'https://github.com/username/network-security-dashboard',
    demo: 'https://demo-security.com',
    category: 'security'
  },
  {
    title: 'E-Commerce Platform with Security Focus',
    description: 'Full-stack e-commerce solution with advanced security features and payment processing',
    image: '/images/project3.jpg',
    tech: ['Laravel', 'Vue.js', 'MySQL', 'Stripe API'],
    features: [
      'PCI DSS compliant payment processing',
      'SQL injection prevention',
      'Rate limiting and DDoS protection', 
      'Encrypted customer data storage'
    ],
    github: 'https://github.com/username/secure-ecommerce',
    demo: 'https://demo-ecommerce.com',
    category: 'web'
  }
];

const isVisible = ref(false);

onMounted(() => {
  setTimeout(() => {
    isVisible.value = true;
  }, 100);
});
</script>

<template>
  <Head title="Home - Portfolio" />
  
  <PortfolioLayout>
    <!-- Hero Section -->
    <section class="relative min-h-screen flex items-center justify-center overflow-hidden">
      <!-- Background gradient -->
      <div class="absolute inset-0 bg-gradient-to-br from-primary/5 via-transparent to-accent/5"></div>
      
      <!-- Animated background elements -->
      <div class="absolute inset-0 overflow-hidden">
        <div class="absolute -top-40 -right-40 w-80 h-80 bg-primary/10 rounded-full blur-3xl animate-pulse"></div>
        <div class="absolute -bottom-40 -left-40 w-80 h-80 bg-accent/10 rounded-full blur-3xl animate-pulse delay-1000"></div>
      </div>

      <div class="relative max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-20">
        <div class="text-center space-y-8">
          <!-- Main heading with animation -->
          <div 
            :class="[
              'transition-all duration-1000 ease-out',
              isVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-8'
            ]"
          >
            <h1 class="text-4xl md:text-6xl lg:text-7xl font-bold tracking-tight">
              <span class="block text-foreground">Software Engineer</span>
              <span class="block bg-gradient-to-r from-primary to-accent bg-clip-text text-transparent">
                Full-Stack | Mobile | Cybersecurity
              </span>
            </h1>
          </div>

          <!-- Subtitle -->
          <div 
            :class="[
              'transition-all duration-1000 ease-out delay-200',
              isVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-8'
            ]"
          >
            <p class="text-xl md:text-2xl text-muted-foreground max-w-3xl mx-auto leading-relaxed">
              I'm a software engineer specializing in full-stack web and mobile development. I build secure, scalable applications using Laravel, Flutter, and modern cloud technologies.
            </p>
          </div>

          <!-- CTA Buttons -->
          <div 
            :class="[
              'flex flex-col sm:flex-row gap-4 justify-center items-center transition-all duration-1000 ease-out delay-400',
              isVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-8'
            ]"
          >
            <Link 
              href="/projects"
              class="group inline-flex items-center gap-2 bg-primary text-primary-foreground px-8 py-4 rounded-lg font-medium hover:bg-primary/90 transition-all duration-200 hover:scale-105 hover:shadow-lg"
            >
              View My Work
              <ArrowRight class="w-4 h-4 group-hover:translate-x-1 transition-transform duration-200" />
            </Link>
            <a 
              href="/resume.pdf" 
              download="John_Doe_Software_Engineer_Resume.pdf"
              class="inline-flex items-center gap-2 border border-border px-8 py-4 rounded-lg font-medium hover:bg-accent transition-all duration-200 hover:scale-105"
            >
              <Download class="w-4 h-4" />
              Download CV
            </a>
          </div>

          <!-- Social proof / stats -->
          <div 
            :class="[
              'grid grid-cols-1 md:grid-cols-3 gap-8 max-w-2xl mx-auto pt-16 transition-all duration-1000 ease-out delay-600',
              isVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-8'
            ]"
          >
            <div class="text-center">
              <div class="text-3xl font-bold text-primary">50+</div>
              <div class="text-sm text-muted-foreground">Projects Completed</div>
            </div>
            <div class="text-center">
              <div class="text-3xl font-bold text-primary">3+</div>
              <div class="text-sm text-muted-foreground">Years Experience</div>
            </div>
            <div class="text-center">
              <div class="text-3xl font-bold text-primary">100%</div>
              <div class="text-sm text-muted-foreground">Client Satisfaction</div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Skills Section -->
    <section id="skills" class="py-20 bg-muted/30">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="text-center mb-16">
          <h2 class="text-3xl md:text-4xl font-bold mb-4">Skills & Technologies</h2>
          <p class="text-lg text-muted-foreground max-w-2xl mx-auto">
            A comprehensive overview of my technical expertise across web, mobile, and cybersecurity domains
          </p>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-8">
          <div 
            v-for="category in skillCategories" 
            :key="category.title"
            class="group p-6 bg-background rounded-xl border border-border hover:border-primary/50 transition-all duration-300 hover:shadow-lg hover:-translate-y-1"
          >
            <h3 class="text-lg font-semibold mb-4 text-primary">{{ category.title }}</h3>
            <div class="space-y-2">
              <span 
                v-for="skill in category.skills" 
                :key="skill"
                class="inline-block bg-muted text-muted-foreground px-3 py-1 rounded-full text-sm mr-2 mb-2 hover:bg-primary/10 hover:text-primary transition-colors duration-200"
              >
                {{ skill }}
              </span>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Certifications Section -->
    <section id="certifications" class="py-20">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="text-center mb-16">
          <h2 class="text-3xl md:text-4xl font-bold mb-4">🎓 Certifications</h2>
          <p class="text-lg text-muted-foreground max-w-2xl mx-auto">
            Verified credentials that demonstrate my expertise in networking and cybersecurity
          </p>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6">
          <div 
            v-for="cert in certifications" 
            :key="cert.title"
            class="group p-6 bg-background rounded-xl border border-border hover:border-primary/50 transition-all duration-300 hover:shadow-lg hover:-translate-y-1 text-center"
          >
            <div class="w-16 h-16 bg-primary/10 rounded-full flex items-center justify-center mx-auto mb-4 group-hover:bg-primary/20 transition-colors duration-300">
              <span class="text-2xl">🏅</span>
            </div>
            <h3 class="font-semibold mb-2 text-primary">{{ cert.title }}</h3>
            <p class="text-sm text-muted-foreground mb-2">{{ cert.issuer }}</p>
            <div class="flex items-center justify-center gap-2">
              <span class="text-xs bg-muted px-2 py-1 rounded-full">{{ cert.year }}</span>
              <span v-if="cert.verified" class="text-xs bg-green-100 text-green-800 px-2 py-1 rounded-full dark:bg-green-900 dark:text-green-200">
                ✓ Verified
              </span>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Featured Projects Section -->
    <section class="py-20">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="text-center mb-16">
          <h2 class="text-3xl md:text-4xl font-bold mb-4">Featured Projects</h2>
          <p class="text-lg text-muted-foreground max-w-2xl mx-auto">
            A selection of my recent work that showcases my skills and creativity
          </p>
        </div>

        <div class="grid grid-cols-1 lg:grid-cols-2 xl:grid-cols-3 gap-8">
          <div 
            v-for="project in featuredProjects" 
            :key="project.title"
            class="group bg-background rounded-xl border border-border overflow-hidden hover:border-primary/50 transition-all duration-300 hover:shadow-xl hover:-translate-y-2"
          >
            <!-- Project Image Placeholder -->
            <div class="aspect-video bg-gradient-to-br from-primary/20 to-accent/20 relative overflow-hidden">
              <div class="absolute inset-0 bg-gradient-to-t from-black/40 to-transparent"></div>
              <div class="absolute top-4 right-4">
                <span 
                  :class="[
                    'px-3 py-1 rounded-full text-xs font-medium',
                    project.category === 'mobile' ? 'bg-blue-100 text-blue-800 dark:bg-blue-900 dark:text-blue-200' :
                    project.category === 'security' ? 'bg-red-100 text-red-800 dark:bg-red-900 dark:text-red-200' :
                    'bg-green-100 text-green-800 dark:bg-green-900 dark:text-green-200'
                  ]"
                >
                  {{ project.category.charAt(0).toUpperCase() + project.category.slice(1) }}
                </span>
              </div>
              <div class="absolute bottom-4 left-4 right-4">
                <div class="flex gap-2 flex-wrap">
                  <span 
                    v-for="tech in project.tech" 
                    :key="tech"
                    class="px-2 py-1 bg-background/90 text-xs rounded-md backdrop-blur-sm"
                  >
                    {{ tech }}
                  </span>
                </div>
              </div>
            </div>

            <div class="p-6">
              <h3 class="text-xl font-semibold mb-2 group-hover:text-primary transition-colors duration-200">
                {{ project.title }}
              </h3>
              <p class="text-muted-foreground mb-4 text-sm leading-relaxed">{{ project.description }}</p>
              
              <!-- Key Features -->
              <div class="mb-4">
                <h4 class="font-medium text-sm mb-2">Key Features:</h4>
                <ul class="space-y-1">
                  <li 
                    v-for="feature in project.features.slice(0, 3)" 
                    :key="feature"
                    class="text-xs text-muted-foreground flex items-start gap-2"
                  >
                    <span class="w-1.5 h-1.5 bg-primary rounded-full mt-1.5 flex-shrink-0"></span>
                    {{ feature }}
                  </li>
                  <li v-if="project.features.length > 3" class="text-xs text-muted-foreground">
                    <span class="text-primary">+{{ project.features.length - 3 }} more features</span>
                  </li>
                </ul>
              </div>
              
              <div class="flex gap-3">
                <a 
                  :href="project.github" 
                  target="_blank"
                  class="inline-flex items-center gap-1 text-sm text-muted-foreground hover:text-foreground transition-colors duration-200"
                >
                  <Github class="w-4 h-4" />
                  Code
                </a>
                <a 
                  :href="project.demo" 
                  target="_blank"
                  class="inline-flex items-center gap-1 text-sm text-muted-foreground hover:text-foreground transition-colors duration-200"
                >
                  <ExternalLink class="w-4 h-4" />
                  Demo
                </a>
              </div>
            </div>
          </div>
        </div>

        <div class="text-center mt-12">
          <Link 
            href="/projects"
            class="inline-flex items-center gap-2 bg-primary text-primary-foreground px-6 py-3 rounded-lg font-medium hover:bg-primary/90 transition-all duration-200 hover:scale-105"
          >
            View All Projects
            <ArrowRight class="w-4 h-4" />
          </Link>
        </div>
      </div>
    </section>

    <!-- Philosophy Section -->
    <section class="py-20 bg-muted/30">
      <div class="max-w-4xl mx-auto px-4 sm:px-6 lg:px-8 text-center">
        <h2 class="text-3xl md:text-4xl font-bold mb-8">My Development Philosophy</h2>
        <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
          <div class="p-6 bg-background rounded-xl border border-border">
            <div class="w-12 h-12 bg-primary/10 rounded-lg flex items-center justify-center mx-auto mb-4">
              <Code class="w-6 h-6 text-primary" />
            </div>
            <h3 class="font-semibold mb-2">Clean, Maintainable Code</h3>
            <p class="text-sm text-muted-foreground">
              I write code that's not just functional, but readable, scalable, and easy to maintain for future developers.
            </p>
          </div>
          <div class="p-6 bg-background rounded-xl border border-border">
            <div class="w-12 h-12 bg-primary/10 rounded-lg flex items-center justify-center mx-auto mb-4">
              <span class="text-xl">🔒</span>
            </div>
            <h3 class="font-semibold mb-2">Security by Design</h3>
            <p class="text-sm text-muted-foreground">
              Security isn't an afterthought—it's built into every layer of the application from the ground up.
            </p>
          </div>
          <div class="p-6 bg-background rounded-xl border border-border">
            <div class="w-12 h-12 bg-primary/10 rounded-lg flex items-center justify-center mx-auto mb-4">
              <Zap class="w-6 h-6 text-primary" />
            </div>
            <h3 class="font-semibold mb-2">Performance & Usability First</h3>
            <p class="text-sm text-muted-foreground">
              Every feature is optimized for speed and user experience, ensuring applications are both fast and intuitive.
            </p>
          </div>
        </div>
      </div>
    </section>

    <!-- CTA Section -->
    <section class="py-20 bg-primary text-primary-foreground">
      <div class="max-w-4xl mx-auto px-4 sm:px-6 lg:px-8 text-center">
        <h2 class="text-3xl md:text-4xl font-bold mb-6">
          Ready to Start Your Project?
        </h2>
        <p class="text-xl mb-8 opacity-90">
          Let's work together to bring your ideas to life with modern design and cutting-edge technology.
        </p>
        <Link 
          href="/contact"
          class="inline-flex items-center gap-2 bg-background text-foreground px-8 py-4 rounded-lg font-medium hover:bg-background/90 transition-all duration-200 hover:scale-105"
        >
          Get In Touch
          <ArrowRight class="w-4 h-4" />
        </Link>
      </div>
    </section>
  </PortfolioLayout>
</template>
