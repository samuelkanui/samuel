<script setup lang="ts">
import { Head } from '@inertiajs/vue3';
import PortfolioLayout from '@/layouts/PortfolioLayout.vue';
import { Calendar, MapPin, Award, Users, Coffee, Code2 } from 'lucide-vue-next';

const experience = [
  {
    title: 'Senior Frontend Developer',
    company: 'Tech Solutions Inc.',
    period: '2022 - Present',
    description: 'Leading frontend development for enterprise applications using Vue.js and React.',
    achievements: ['Led team of 5 developers', 'Improved performance by 40%', 'Implemented design system']
  },
  {
    title: 'Full Stack Developer',
    company: 'Digital Agency Co.',
    period: '2020 - 2022',
    description: 'Developed web applications using Laravel, Vue.js, and modern frontend technologies.',
    achievements: ['Built 15+ client projects', 'Mentored junior developers', 'Introduced CI/CD pipeline']
  },
  {
    title: 'Junior Developer',
    company: 'StartUp Labs',
    period: '2019 - 2020',
    description: 'Started career building responsive websites and learning modern web technologies.',
    achievements: ['Completed 20+ projects', 'Learned Vue.js & Laravel', 'Contributed to open source']
  }
];

const skills = [
  { category: 'Frontend', items: ['Vue.js', 'React', 'TypeScript', 'TailwindCSS', 'Nuxt.js', 'Next.js'] },
  { category: 'Backend', items: ['Laravel', 'Node.js', 'PHP', 'Python', 'MySQL', 'PostgreSQL'] },
  { category: 'Tools', items: ['Git', 'Docker', 'AWS', 'Figma', 'Vite', 'Webpack'] },
  { category: 'Soft Skills', items: ['Team Leadership', 'Problem Solving', 'Communication', 'Mentoring'] }
];

const stats = [
  { icon: Code2, label: 'Lines of Code', value: '500K+' },
  { icon: Coffee, label: 'Cups of Coffee', value: '2,847' },
  { icon: Users, label: 'Happy Clients', value: '50+' },
  { icon: Award, label: 'Projects Completed', value: '100+' }
];
</script>

<template>
  <Head title="About - Portfolio" />
  
  <PortfolioLayout>
    <!-- Hero Section -->
    <section class="pt-20 pb-16 bg-gradient-to-br from-primary/5 via-transparent to-accent/5">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="grid grid-cols-1 lg:grid-cols-2 gap-12 items-center">
          <!-- Content -->
          <div class="space-y-6">
            <h1 class="text-4xl md:text-5xl font-bold tracking-tight">
              About <span class="bg-gradient-to-r from-primary to-accent bg-clip-text text-transparent">Me</span>
            </h1>
            <p class="text-xl text-muted-foreground leading-relaxed">
              I'm a passionate full-stack developer with over 3 years of experience creating digital solutions that make a difference. I love turning complex problems into simple, beautiful, and intuitive designs.
            </p>
            <div class="flex flex-wrap gap-4 text-sm text-muted-foreground">
              <div class="flex items-center gap-2">
                <MapPin class="w-4 h-4" />
                <span>San Francisco, CA</span>
              </div>
              <div class="flex items-center gap-2">
                <Calendar class="w-4 h-4" />
                <span>Available for freelance</span>
              </div>
            </div>
          </div>

          <!-- Profile Image Placeholder -->
          <div class="relative">
            <div class="aspect-square bg-gradient-to-br from-primary/20 to-accent/20 rounded-2xl relative overflow-hidden">
              <div class="absolute inset-0 bg-gradient-to-t from-black/10 to-transparent"></div>
              <div class="absolute bottom-6 left-6 right-6">
                <div class="bg-background/90 backdrop-blur-sm rounded-lg p-4">
                  <p class="text-sm font-medium">Currently working on</p>
                  <p class="text-xs text-muted-foreground">Next-gen e-commerce platform</p>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Stats Section -->
    <section class="py-16 bg-muted/30">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="grid grid-cols-2 md:grid-cols-4 gap-8">
          <div 
            v-for="stat in stats" 
            :key="stat.label"
            class="text-center group"
          >
            <div class="flex items-center justify-center w-12 h-12 bg-primary/10 rounded-lg mx-auto mb-4 group-hover:bg-primary/20 transition-colors duration-300">
              <component :is="stat.icon" class="w-6 h-6 text-primary" />
            </div>
            <div class="text-2xl md:text-3xl font-bold text-primary mb-1">{{ stat.value }}</div>
            <div class="text-sm text-muted-foreground">{{ stat.label }}</div>
          </div>
        </div>
      </div>
    </section>

    <!-- Experience Section -->
    <section class="py-20">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="text-center mb-16">
          <h2 class="text-3xl md:text-4xl font-bold mb-4">Experience</h2>
          <p class="text-lg text-muted-foreground max-w-2xl mx-auto">
            My journey in the world of web development and the milestones I've achieved
          </p>
        </div>

        <div class="space-y-8">
          <div 
            v-for="(job, index) in experience" 
            :key="index"
            class="relative pl-8 pb-8 border-l-2 border-border last:border-l-0 last:pb-0"
          >
            <!-- Timeline dot -->
            <div class="absolute -left-2 top-0 w-4 h-4 bg-primary rounded-full border-4 border-background"></div>
            
            <div class="bg-background rounded-xl border border-border p-6 hover:border-primary/50 transition-colors duration-300">
              <div class="flex flex-col md:flex-row md:items-center md:justify-between mb-4">
                <div>
                  <h3 class="text-xl font-semibold">{{ job.title }}</h3>
                  <p class="text-primary font-medium">{{ job.company }}</p>
                </div>
                <span class="text-sm text-muted-foreground bg-muted px-3 py-1 rounded-full mt-2 md:mt-0">
                  {{ job.period }}
                </span>
              </div>
              
              <p class="text-muted-foreground mb-4">{{ job.description }}</p>
              
              <div class="space-y-2">
                <h4 class="font-medium text-sm">Key Achievements:</h4>
                <ul class="space-y-1">
                  <li 
                    v-for="achievement in job.achievements" 
                    :key="achievement"
                    class="text-sm text-muted-foreground flex items-start gap-2"
                  >
                    <span class="w-1.5 h-1.5 bg-primary rounded-full mt-2 flex-shrink-0"></span>
                    {{ achievement }}
                  </li>
                </ul>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Skills Section -->
    <section class="py-20 bg-muted/30">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="text-center mb-16">
          <h2 class="text-3xl md:text-4xl font-bold mb-4">Skills & Technologies</h2>
          <p class="text-lg text-muted-foreground max-w-2xl mx-auto">
            The tools and technologies I use to bring ideas to life
          </p>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-8">
          <div 
            v-for="skillGroup in skills" 
            :key="skillGroup.category"
            class="bg-background rounded-xl border border-border p-6 hover:border-primary/50 transition-colors duration-300"
          >
            <h3 class="font-semibold mb-4 text-primary">{{ skillGroup.category }}</h3>
            <div class="space-y-2">
              <span 
                v-for="skill in skillGroup.items" 
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

    <!-- Personal Section -->
    <section class="py-20">
      <div class="max-w-4xl mx-auto px-4 sm:px-6 lg:px-8 text-center">
        <h2 class="text-3xl md:text-4xl font-bold mb-6">Beyond Code</h2>
        <p class="text-lg text-muted-foreground mb-8 leading-relaxed">
          When I'm not coding, you can find me exploring new technologies, contributing to open-source projects, 
          or enjoying a good cup of coffee while reading about the latest web development trends. I believe in 
          continuous learning and staying updated with the ever-evolving tech landscape.
        </p>
        <p class="text-lg text-muted-foreground leading-relaxed">
          I'm passionate about mentoring junior developers and sharing knowledge through blog posts and 
          community contributions. Let's connect and build something amazing together!
        </p>
      </div>
    </section>
  </PortfolioLayout>
</template>
