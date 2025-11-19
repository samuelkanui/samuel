<script setup lang="ts">
import { ref } from 'vue';
import { Head } from '@inertiajs/vue3';
import PortfolioLayout from '@/layouts/PortfolioLayout.vue';
import { Mail, Phone, MapPin, Send, Github, Linkedin, Twitter, Clock } from 'lucide-vue-next';

const form = ref({
  name: '',
  email: '',
  subject: '',
  message: ''
});

const isSubmitting = ref(false);

const contactInfo = [
  {
    icon: Mail,
    label: 'Email',
    value: 'hello@example.com',
    href: 'mailto:hello@example.com'
  },
  {
    icon: Phone,
    label: 'Phone',
    value: '+1 (555) 123-4567',
    href: 'tel:+15551234567'
  },
  {
    icon: MapPin,
    label: 'Location',
    value: 'San Francisco, CA',
    href: 'https://maps.google.com'
  },
  {
    icon: Clock,
    label: 'Response Time',
    value: 'Within 24 hours',
    href: null
  }
];

const socialLinks = [
  {
    icon: Github,
    label: 'GitHub',
    href: 'https://github.com/username',
    color: 'hover:text-gray-900 dark:hover:text-white'
  },
  {
    icon: Linkedin,
    label: 'LinkedIn',
    href: 'https://linkedin.com/in/username',
    color: 'hover:text-blue-600'
  },
  {
    icon: Twitter,
    label: 'Twitter',
    href: 'https://twitter.com/username',
    color: 'hover:text-blue-400'
  }
];

const submitForm = async () => {
  isSubmitting.value = true;
  
  // Simulate form submission
  await new Promise(resolve => setTimeout(resolve, 2000));
  
  // Reset form
  form.value = {
    name: '',
    email: '',
    subject: '',
    message: ''
  };
  
  isSubmitting.value = false;
  
  // Show success message (you can implement toast notifications here)
  alert('Thank you for your message! I\'ll get back to you soon.');
};
</script>

<template>
  <Head title="Contact - Portfolio" />
  
  <PortfolioLayout>
    <!-- Hero Section -->
    <section class="pt-20 pb-16 bg-gradient-to-br from-primary/5 via-transparent to-accent/5">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 text-center">
        <h1 class="text-4xl md:text-5xl font-bold tracking-tight mb-6">
          Get In <span class="bg-gradient-to-r from-primary to-accent bg-clip-text text-transparent">Touch</span>
        </h1>
        <p class="text-xl text-muted-foreground max-w-3xl mx-auto leading-relaxed">
          Have a project in mind or just want to say hello? I'd love to hear from you. 
          Let's discuss how we can work together to bring your ideas to life.
        </p>
      </div>
    </section>

    <!-- Contact Content -->
    <section class="py-20">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="grid grid-cols-1 lg:grid-cols-2 gap-16">
          <!-- Contact Information -->
          <div class="space-y-8">
            <div>
              <h2 class="text-3xl font-bold mb-6">Let's Start a Conversation</h2>
              <p class="text-lg text-muted-foreground leading-relaxed">
                I'm always excited to work on new projects and collaborate with amazing people. 
                Whether you have a specific project in mind or just want to explore possibilities, 
                I'm here to help turn your vision into reality.
              </p>
            </div>

            <!-- Contact Details -->
            <div class="space-y-6">
              <div 
                v-for="contact in contactInfo" 
                :key="contact.label"
                class="flex items-center gap-4 p-4 bg-background rounded-xl border border-border hover:border-primary/50 transition-colors duration-300"
              >
                <div class="flex items-center justify-center w-12 h-12 bg-primary/10 rounded-lg">
                  <component :is="contact.icon" class="w-6 h-6 text-primary" />
                </div>
                <div>
                  <p class="font-medium">{{ contact.label }}</p>
                  <a 
                    v-if="contact.href"
                    :href="contact.href"
                    class="text-muted-foreground hover:text-primary transition-colors duration-200"
                  >
                    {{ contact.value }}
                  </a>
                  <p v-else class="text-muted-foreground">{{ contact.value }}</p>
                </div>
              </div>
            </div>

            <!-- Social Links -->
            <div>
              <h3 class="font-semibold mb-4">Follow Me</h3>
              <div class="flex gap-4">
                <a
                  v-for="social in socialLinks"
                  :key="social.label"
                  :href="social.href"
                  target="_blank"
                  :class="[
                    'flex items-center justify-center w-12 h-12 bg-background border border-border rounded-lg transition-all duration-200 hover:scale-105',
                    social.color
                  ]"
                  :title="social.label"
                >
                  <component :is="social.icon" class="w-5 h-5" />
                </a>
              </div>
            </div>

            <!-- Availability -->
            <div class="p-6 bg-primary/5 rounded-xl border border-primary/20">
              <h3 class="font-semibold text-primary mb-2">Current Availability</h3>
              <p class="text-sm text-muted-foreground">
                I'm currently available for new projects and collaborations. 
                My typical response time is within 24 hours.
              </p>
            </div>
          </div>

          <!-- Contact Form -->
          <div class="bg-background rounded-2xl border border-border p-8 shadow-lg">
            <h3 class="text-2xl font-bold mb-6">Send Me a Message</h3>
            
            <form @submit.prevent="submitForm" class="space-y-6">
              <!-- Name -->
              <div>
                <label for="name" class="block text-sm font-medium mb-2">
                  Full Name *
                </label>
                <input
                  id="name"
                  v-model="form.name"
                  type="text"
                  required
                  class="w-full px-4 py-3 bg-background border border-border rounded-lg focus:outline-none focus:ring-2 focus:ring-primary/20 focus:border-primary transition-colors duration-200"
                  placeholder="Your full name"
                />
              </div>

              <!-- Email -->
              <div>
                <label for="email" class="block text-sm font-medium mb-2">
                  Email Address *
                </label>
                <input
                  id="email"
                  v-model="form.email"
                  type="email"
                  required
                  class="w-full px-4 py-3 bg-background border border-border rounded-lg focus:outline-none focus:ring-2 focus:ring-primary/20 focus:border-primary transition-colors duration-200"
                  placeholder="your.email@example.com"
                />
              </div>

              <!-- Subject -->
              <div>
                <label for="subject" class="block text-sm font-medium mb-2">
                  Subject *
                </label>
                <input
                  id="subject"
                  v-model="form.subject"
                  type="text"
                  required
                  class="w-full px-4 py-3 bg-background border border-border rounded-lg focus:outline-none focus:ring-2 focus:ring-primary/20 focus:border-primary transition-colors duration-200"
                  placeholder="What's this about?"
                />
              </div>

              <!-- Message -->
              <div>
                <label for="message" class="block text-sm font-medium mb-2">
                  Message *
                </label>
                <textarea
                  id="message"
                  v-model="form.message"
                  rows="6"
                  required
                  class="w-full px-4 py-3 bg-background border border-border rounded-lg focus:outline-none focus:ring-2 focus:ring-primary/20 focus:border-primary transition-colors duration-200 resize-none"
                  placeholder="Tell me about your project or idea..."
                ></textarea>
              </div>

              <!-- Submit Button -->
              <button
                type="submit"
                :disabled="isSubmitting"
                :class="[
                  'w-full inline-flex items-center justify-center gap-2 px-8 py-4 rounded-lg font-medium transition-all duration-200',
                  isSubmitting
                    ? 'bg-muted text-muted-foreground cursor-not-allowed'
                    : 'bg-primary text-primary-foreground hover:bg-primary/90 hover:scale-105'
                ]"
              >
                <Send class="w-4 h-4" />
                {{ isSubmitting ? 'Sending...' : 'Send Message' }}
              </button>
            </form>

            <p class="text-xs text-muted-foreground mt-4">
              * Required fields. I respect your privacy and will never share your information.
            </p>
          </div>
        </div>
      </div>
    </section>

    <!-- FAQ Section -->
    <section class="py-20 bg-muted/30">
      <div class="max-w-4xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="text-center mb-16">
          <h2 class="text-3xl md:text-4xl font-bold mb-4">Frequently Asked Questions</h2>
          <p class="text-lg text-muted-foreground">
            Quick answers to common questions about working together
          </p>
        </div>

        <div class="space-y-6">
          <div class="bg-background rounded-xl border border-border p-6">
            <h3 class="font-semibold mb-2">What's your typical project timeline?</h3>
            <p class="text-muted-foreground">
              Project timelines vary depending on scope and complexity. A simple website might take 2-4 weeks, 
              while a complex web application could take 2-6 months. I'll provide a detailed timeline during our initial consultation.
            </p>
          </div>

          <div class="bg-background rounded-xl border border-border p-6">
            <h3 class="font-semibold mb-2">Do you work with international clients?</h3>
            <p class="text-muted-foreground">
              Absolutely! I work with clients worldwide and am comfortable with remote collaboration. 
              I'm flexible with time zones and use modern communication tools to ensure smooth project delivery.
            </p>
          </div>

          <div class="bg-background rounded-xl border border-border p-6">
            <h3 class="font-semibold mb-2">What technologies do you specialize in?</h3>
            <p class="text-muted-foreground">
              I specialize in modern web technologies including Vue.js, React, Laravel, Node.js, and TypeScript. 
              I'm always learning new technologies to provide the best solutions for each project.
            </p>
          </div>

          <div class="bg-background rounded-xl border border-border p-6">
            <h3 class="font-semibold mb-2">Do you provide ongoing support?</h3>
            <p class="text-muted-foreground">
              Yes! I offer ongoing maintenance and support packages to ensure your project continues to run smoothly. 
              This includes updates, bug fixes, and feature enhancements as needed.
            </p>
          </div>
        </div>
      </div>
    </section>
  </PortfolioLayout>
</template>
