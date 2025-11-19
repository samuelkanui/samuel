<script setup lang="ts">
import { ref, onMounted } from 'vue';
import { Link, usePage } from '@inertiajs/vue3';
import { Menu, X, Github, Linkedin, Mail, Sun, Moon } from 'lucide-vue-next';

const isMenuOpen = ref(false);
const isDark = ref(false);

const page = usePage();

const navigation = [
  { name: 'Home', href: '/', current: false },
  { name: 'About', href: '/about', current: false },
  { name: 'Projects', href: '/projects', current: false },
  { name: 'Skills', href: '/#skills', current: false },
  { name: 'Certifications', href: '/#certifications', current: false },
  { name: 'Contact', href: '/contact', current: false },
];

const toggleTheme = () => {
  isDark.value = !isDark.value;
  document.documentElement.classList.toggle('dark');
  localStorage.setItem('theme', isDark.value ? 'dark' : 'light');
};

onMounted(() => {
  const savedTheme = localStorage.getItem('theme');
  const prefersDark = window.matchMedia('(prefers-color-scheme: dark)').matches;
  
  isDark.value = savedTheme === 'dark' || (!savedTheme && prefersDark);
  
  if (isDark.value) {
    document.documentElement.classList.add('dark');
  }
});

// Update current navigation item based on current route
const updateCurrentNav = () => {
  const currentPath = page.url;
  navigation.forEach(item => {
    item.current = item.href === currentPath || (item.href !== '/' && currentPath.startsWith(item.href));
  });
};

updateCurrentNav();
</script>

<template>
  <div class="min-h-screen bg-background text-foreground">
    <!-- Navigation -->
    <nav class="fixed top-0 w-full z-50 bg-background/80 backdrop-blur-md border-b border-border">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="flex justify-between items-center h-16">
          <!-- Logo -->
          <Link href="/" class="flex items-center space-x-2">
            <div class="w-8 h-8 bg-primary rounded-lg flex items-center justify-center">
              <span class="text-primary-foreground font-bold text-lg">P</span>
            </div>
            <span class="font-semibold text-xl">Portfolio</span>
          </Link>

          <!-- Desktop Navigation -->
          <div class="hidden md:flex items-center space-x-8">
            <div class="flex space-x-6">
              <Link
                v-for="item in navigation"
                :key="item.name"
                :href="item.href"
                :class="[
                  'px-3 py-2 rounded-md text-sm font-medium transition-colors duration-200',
                  item.current
                    ? 'text-primary bg-primary/10'
                    : 'text-muted-foreground hover:text-foreground hover:bg-accent'
                ]"
              >
                {{ item.name }}
              </Link>
            </div>
            
            <!-- Theme Toggle -->
            <button
              @click="toggleTheme"
              class="p-2 rounded-md text-muted-foreground hover:text-foreground hover:bg-accent transition-colors duration-200"
            >
              <Sun v-if="isDark" class="h-5 w-5" />
              <Moon v-else class="h-5 w-5" />
            </button>
          </div>

          <!-- Mobile menu button -->
          <div class="md:hidden flex items-center space-x-2">
            <button
              @click="toggleTheme"
              class="p-2 rounded-md text-muted-foreground hover:text-foreground hover:bg-accent transition-colors duration-200"
            >
              <Sun v-if="isDark" class="h-5 w-5" />
              <Moon v-else class="h-5 w-5" />
            </button>
            <button
              @click="isMenuOpen = !isMenuOpen"
              class="p-2 rounded-md text-muted-foreground hover:text-foreground hover:bg-accent transition-colors duration-200"
            >
              <Menu v-if="!isMenuOpen" class="h-6 w-6" />
              <X v-else class="h-6 w-6" />
            </button>
          </div>
        </div>
      </div>

      <!-- Mobile Navigation Menu -->
      <div
        v-if="isMenuOpen"
        class="md:hidden bg-background border-t border-border"
      >
        <div class="px-2 pt-2 pb-3 space-y-1">
          <Link
            v-for="item in navigation"
            :key="item.name"
            :href="item.href"
            :class="[
              'block px-3 py-2 rounded-md text-base font-medium transition-colors duration-200',
              item.current
                ? 'text-primary bg-primary/10'
                : 'text-muted-foreground hover:text-foreground hover:bg-accent'
            ]"
            @click="isMenuOpen = false"
          >
            {{ item.name }}
          </Link>
        </div>
      </div>
    </nav>

    <!-- Main Content -->
    <main class="pt-16">
      <slot />
    </main>

    <!-- Footer -->
    <footer class="bg-muted/50 border-t border-border">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-12">
        <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
          <!-- Brand -->
          <div class="space-y-4">
            <Link href="/" class="flex items-center space-x-2">
              <div class="w-8 h-8 bg-primary rounded-lg flex items-center justify-center">
                <span class="text-primary-foreground font-bold text-lg">P</span>
              </div>
              <span class="font-semibold text-xl">Portfolio</span>
            </Link>
            <p class="text-muted-foreground text-sm">
              Crafting digital experiences with passion and precision.
            </p>
          </div>

          <!-- Quick Links -->
          <div class="space-y-4">
            <h3 class="font-semibold">Quick Links</h3>
            <div class="space-y-2">
              <Link
                v-for="item in navigation"
                :key="item.name"
                :href="item.href"
                class="block text-sm text-muted-foreground hover:text-foreground transition-colors duration-200"
              >
                {{ item.name }}
              </Link>
            </div>
          </div>

          <!-- Social Links -->
          <div class="space-y-4">
            <h3 class="font-semibold">Connect</h3>
            <div class="flex space-x-4">
              <a
                href="#"
                class="p-2 rounded-md text-muted-foreground hover:text-foreground hover:bg-accent transition-colors duration-200"
              >
                <Github class="h-5 w-5" />
              </a>
              <a
                href="#"
                class="p-2 rounded-md text-muted-foreground hover:text-foreground hover:bg-accent transition-colors duration-200"
              >
                <Linkedin class="h-5 w-5" />
              </a>
              <a
                href="#"
                class="p-2 rounded-md text-muted-foreground hover:text-foreground hover:bg-accent transition-colors duration-200"
              >
                <Mail class="h-5 w-5" />
              </a>
            </div>
          </div>
        </div>

        <div class="mt-8 pt-8 border-t border-border">
          <p class="text-center text-sm text-muted-foreground">
            © {{ new Date().getFullYear() }} Portfolio. All rights reserved.
          </p>
        </div>
      </div>
    </footer>
  </div>
</template>
