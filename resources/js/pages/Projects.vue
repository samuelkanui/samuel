<script setup lang="ts">
import { ref, computed } from 'vue';
import { Head } from '@inertiajs/vue3';
import PortfolioLayout from '@/layouts/PortfolioLayout.vue';
import { Github, ExternalLink, Search } from 'lucide-vue-next';

const searchQuery = ref('');
const selectedCategory = ref('all');

const categories = [
  { id: 'all', name: 'All Projects' },
  { id: 'web', name: 'Web Apps' },
  { id: 'mobile', name: 'Mobile' },
  { id: 'ecommerce', name: 'E-Commerce' },
  { id: 'dashboard', name: 'Dashboards' }
];

const projects = [
  {
    id: 1,
    title: 'E-Commerce Platform',
    description: 'A modern e-commerce solution built with Vue.js and Laravel, featuring real-time inventory management, payment processing, and admin dashboard.',
    image: '/images/project1.jpg',
    category: 'ecommerce',
    tech: ['Vue.js', 'Laravel', 'TailwindCSS', 'Stripe', 'MySQL'],
    github: 'https://github.com/username/ecommerce-platform',
    demo: 'https://demo-ecommerce.com',
    featured: true
  },
  {
    id: 2,
    title: 'Task Management Dashboard',
    description: 'Collaborative project management tool with real-time updates, team collaboration features, and advanced analytics.',
    image: '/images/project2.jpg',
    category: 'dashboard',
    tech: ['React', 'Node.js', 'Socket.io', 'MongoDB', 'Chart.js'],
    github: 'https://github.com/username/task-manager',
    demo: 'https://demo-taskmanager.com',
    featured: true
  },
  {
    id: 3,
    title: 'Mobile Banking App',
    description: 'Secure mobile banking application with biometric authentication, transaction history, and budget tracking.',
    image: '/images/project3.jpg',
    category: 'mobile',
    tech: ['React Native', 'Firebase', 'Redux', 'Expo'],
    github: 'https://github.com/username/banking-app',
    demo: 'https://demo-banking.com',
    featured: false
  },
  {
    id: 4,
    title: 'Portfolio Website',
    description: 'Responsive portfolio website with modern animations, dark mode support, and optimized performance.',
    image: '/images/project4.jpg',
    category: 'web',
    tech: ['Vue.js', 'Nuxt.js', 'GSAP', 'TailwindCSS'],
    github: 'https://github.com/username/portfolio',
    demo: 'https://demo-portfolio.com',
    featured: false
  },
  {
    id: 5,
    title: 'Restaurant Management System',
    description: 'Complete restaurant management solution with order tracking, inventory management, and customer analytics.',
    image: '/images/project5.jpg',
    category: 'web',
    tech: ['Laravel', 'Vue.js', 'MySQL', 'Pusher'],
    github: 'https://github.com/username/restaurant-system',
    demo: 'https://demo-restaurant.com',
    featured: false
  },
  {
    id: 6,
    title: 'Crypto Trading Dashboard',
    description: 'Real-time cryptocurrency trading dashboard with live price feeds, portfolio tracking, and trading signals.',
    image: '/images/project6.jpg',
    category: 'dashboard',
    tech: ['React', 'TypeScript', 'WebSocket', 'D3.js'],
    github: 'https://github.com/username/crypto-dashboard',
    demo: 'https://demo-crypto.com',
    featured: true
  }
];

const filteredProjects = computed(() => {
  let filtered = projects;
  
  if (selectedCategory.value !== 'all') {
    filtered = filtered.filter(project => project.category === selectedCategory.value);
  }
  
  if (searchQuery.value) {
    filtered = filtered.filter(project => 
      project.title.toLowerCase().includes(searchQuery.value.toLowerCase()) ||
      project.description.toLowerCase().includes(searchQuery.value.toLowerCase()) ||
      project.tech.some(tech => tech.toLowerCase().includes(searchQuery.value.toLowerCase()))
    );
  }
  
  return filtered;
});

const featuredProjects = computed(() => projects.filter(project => project.featured));
</script>

<template>
  <Head title="Projects - Portfolio" />
  
  <PortfolioLayout>
    <!-- Hero Section -->
    <section class="pt-20 pb-16 bg-gradient-to-br from-primary/5 via-transparent to-accent/5">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 text-center">
        <h1 class="text-4xl md:text-5xl font-bold tracking-tight mb-6">
          My <span class="bg-gradient-to-r from-primary to-accent bg-clip-text text-transparent">Projects</span>
        </h1>
        <p class="text-xl text-muted-foreground max-w-3xl mx-auto leading-relaxed">
          A showcase of my work, featuring web applications, mobile apps, and digital solutions 
          that demonstrate my skills and passion for creating exceptional user experiences.
        </p>
      </div>
    </section>

    <!-- Featured Projects -->
    <section class="py-16">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="text-center mb-12">
          <h2 class="text-3xl md:text-4xl font-bold mb-4">Featured Projects</h2>
          <p class="text-lg text-muted-foreground">
            Highlighting some of my most impactful and innovative work
          </p>
        </div>

        <div class="grid grid-cols-1 lg:grid-cols-2 gap-8 mb-16">
          <div 
            v-for="project in featuredProjects.slice(0, 2)" 
            :key="project.id"
            class="group bg-background rounded-2xl border border-border overflow-hidden hover:border-primary/50 transition-all duration-300 hover:shadow-2xl hover:-translate-y-1"
          >
            <!-- Project Image -->
            <div class="aspect-video bg-gradient-to-br from-primary/20 to-accent/20 relative overflow-hidden">
              <div class="absolute inset-0 bg-gradient-to-t from-black/40 to-transparent"></div>
              <div class="absolute top-4 right-4">
                <span class="bg-primary text-primary-foreground px-3 py-1 rounded-full text-xs font-medium">
                  Featured
                </span>
              </div>
              <div class="absolute bottom-4 left-4 right-4">
                <div class="flex gap-2 flex-wrap">
                  <span 
                    v-for="tech in project.tech.slice(0, 3)" 
                    :key="tech"
                    class="px-2 py-1 bg-background/90 text-xs rounded-md backdrop-blur-sm"
                  >
                    {{ tech }}
                  </span>
                  <span 
                    v-if="project.tech.length > 3"
                    class="px-2 py-1 bg-background/90 text-xs rounded-md backdrop-blur-sm"
                  >
                    +{{ project.tech.length - 3 }}
                  </span>
                </div>
              </div>
            </div>

            <div class="p-8">
              <h3 class="text-2xl font-semibold mb-3 group-hover:text-primary transition-colors duration-200">
                {{ project.title }}
              </h3>
              <p class="text-muted-foreground mb-6 leading-relaxed">{{ project.description }}</p>
              
              <div class="flex gap-4">
                <a 
                  :href="project.github" 
                  target="_blank"
                  class="inline-flex items-center gap-2 px-4 py-2 border border-border rounded-lg text-sm font-medium hover:bg-accent transition-colors duration-200"
                >
                  <Github class="w-4 h-4" />
                  Code
                </a>
                <a 
                  :href="project.demo" 
                  target="_blank"
                  class="inline-flex items-center gap-2 bg-primary text-primary-foreground px-4 py-2 rounded-lg text-sm font-medium hover:bg-primary/90 transition-colors duration-200"
                >
                  <ExternalLink class="w-4 h-4" />
                  Live Demo
                </a>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- All Projects -->
    <section class="py-16 bg-muted/30">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="text-center mb-12">
          <h2 class="text-3xl md:text-4xl font-bold mb-4">All Projects</h2>
          <p class="text-lg text-muted-foreground">
            Explore my complete portfolio of work
          </p>
        </div>

        <!-- Filters -->
        <div class="flex flex-col md:flex-row gap-4 mb-12">
          <!-- Search -->
          <div class="relative flex-1">
            <Search class="absolute left-3 top-1/2 transform -translate-y-1/2 text-muted-foreground w-4 h-4" />
            <input
              v-model="searchQuery"
              type="text"
              placeholder="Search projects..."
              class="w-full pl-10 pr-4 py-3 bg-background border border-border rounded-lg focus:outline-none focus:ring-2 focus:ring-primary/20 focus:border-primary"
            />
          </div>

          <!-- Category Filter -->
          <div class="flex gap-2 flex-wrap">
            <button
              v-for="category in categories"
              :key="category.id"
              @click="selectedCategory = category.id"
              :class="[
                'px-4 py-3 rounded-lg text-sm font-medium transition-colors duration-200',
                selectedCategory === category.id
                  ? 'bg-primary text-primary-foreground'
                  : 'bg-background border border-border hover:bg-accent'
              ]"
            >
              {{ category.name }}
            </button>
          </div>
        </div>

        <!-- Projects Grid -->
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
          <div 
            v-for="project in filteredProjects" 
            :key="project.id"
            class="group bg-background rounded-xl border border-border overflow-hidden hover:border-primary/50 transition-all duration-300 hover:shadow-xl hover:-translate-y-2"
          >
            <!-- Project Image -->
            <div class="aspect-video bg-gradient-to-br from-primary/20 to-accent/20 relative overflow-hidden">
              <div class="absolute inset-0 bg-gradient-to-t from-black/20 to-transparent"></div>
              <div class="absolute bottom-3 left-3 right-3">
                <div class="flex gap-1 flex-wrap">
                  <span 
                    v-for="tech in project.tech.slice(0, 2)" 
                    :key="tech"
                    class="px-2 py-1 bg-background/90 text-xs rounded-md"
                  >
                    {{ tech }}
                  </span>
                  <span 
                    v-if="project.tech.length > 2"
                    class="px-2 py-1 bg-background/90 text-xs rounded-md"
                  >
                    +{{ project.tech.length - 2 }}
                  </span>
                </div>
              </div>
            </div>

            <div class="p-6">
              <h3 class="text-xl font-semibold mb-2 group-hover:text-primary transition-colors duration-200">
                {{ project.title }}
              </h3>
              <p class="text-muted-foreground text-sm mb-4 line-clamp-2">{{ project.description }}</p>
              
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

        <!-- No Results -->
        <div 
          v-if="filteredProjects.length === 0"
          class="text-center py-16"
        >
          <div class="text-6xl mb-4">🔍</div>
          <h3 class="text-xl font-semibold mb-2">No projects found</h3>
          <p class="text-muted-foreground">Try adjusting your search or filter criteria</p>
        </div>
      </div>
    </section>

    <!-- CTA Section -->
    <section class="py-20">
      <div class="max-w-4xl mx-auto px-4 sm:px-6 lg:px-8 text-center">
        <h2 class="text-3xl md:text-4xl font-bold mb-6">
          Like What You See?
        </h2>
        <p class="text-xl text-muted-foreground mb-8">
          Let's collaborate on your next project and create something amazing together.
        </p>
        <div class="flex flex-col sm:flex-row gap-4 justify-center">
          <a 
            href="/contact"
            class="inline-flex items-center gap-2 bg-primary text-primary-foreground px-8 py-4 rounded-lg font-medium hover:bg-primary/90 transition-all duration-200 hover:scale-105"
          >
            Start a Project
          </a>
          <a 
            href="mailto:hello@example.com"
            class="inline-flex items-center gap-2 border border-border px-8 py-4 rounded-lg font-medium hover:bg-accent transition-all duration-200 hover:scale-105"
          >
            Send Email
          </a>
        </div>
      </div>
    </section>
  </PortfolioLayout>
</template>

<style scoped>
.line-clamp-2 {
  display: -webkit-box;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
  overflow: hidden;
}
</style>
