<template>
  <q-layout view="hHh lpR fff" class="bg-white">
    <!-- Header -->
    <q-header elevated class="bg-primary text-white q-py-sm" height-hint="64">
      <q-toolbar class="q-px-lg">
        <q-btn flat no-caps no-wrap class="q-mr-sm" to="/">
          <q-icon name="school" size="28px" class="q-mr-sm" />
          <q-toolbar-title shrink class="text-weight-bold text-h5 font-heading">
            ClassMate
          </q-toolbar-title>
        </q-btn>

        <q-space />

        <!-- Desktop Navigation -->
        <div class="gt-sm q-gutter-x-md flex flex-center">
          <q-btn flat no-caps label="Home" class="text-weight-medium" />
          <q-btn flat no-caps label="Features" class="text-weight-medium" />
          <q-btn flat no-caps label="Tutors" class="text-weight-medium" />
          <q-btn flat no-caps label="Classes" class="text-weight-medium" />
          <q-btn unelevated color="accent" text-color="dark" label="Login" to="/login" class="q-ml-md q-px-lg text-weight-bold" />
        </div>

        <!-- Mobile Menu Button -->
        <q-btn flat dense round icon="menu" aria-label="Menu" class="lt-md" @click="toggleMobileMenu" />
      </q-toolbar>
    </q-header>

    <!-- Mobile Navigation Drawer -->
    <q-drawer v-model="mobileMenuOpen" side="right" overlay bordered class="bg-white text-dark">
      <div class="q-pa-md flex justify-between items-center bg-grey-1">
         <div class="text-h6 text-weight-bold font-heading">Menu</div>
         <q-btn flat round dense icon="close" @click="toggleMobileMenu" />
      </div>

      <q-list separator padding>
        <q-item clickable v-close-popup class="q-py-md">
           <q-item-section avatar><q-icon name="home" color="primary" /></q-item-section>
           <q-item-section class="text-subtitle1 text-weight-medium">Home</q-item-section>
        </q-item>
        <q-item clickable v-close-popup class="q-py-md">
           <q-item-section avatar><q-icon name="star" color="primary" /></q-item-section>
           <q-item-section class="text-subtitle1 text-weight-medium">Features</q-item-section>
        </q-item>
        <q-item clickable v-close-popup class="q-py-md">
           <q-item-section avatar><q-icon name="school" color="primary" /></q-item-section>
           <q-item-section class="text-subtitle1 text-weight-medium">Tutors</q-item-section>
        </q-item>
        <q-item clickable v-close-popup class="q-py-md">
           <q-item-section avatar><q-icon name="class" color="primary" /></q-item-section>
           <q-item-section class="text-subtitle1 text-weight-medium">Classes</q-item-section>
        </q-item>
        
        <q-item class="q-mt-md">
           <q-btn unelevated color="accent" text-color="dark" label="Login / Register" to="/login" class="full-width text-weight-bold" />
        </q-item>
      </q-list>
    </q-drawer>

    <!-- Page Container -->
    <q-page-container>
      <router-view />
    </q-page-container>


    <!-- Footer -->
    <q-footer class="bg-dark text-white q-py-lg">
      <div class="container q-px-lg">
        <div class="row q-col-gutter-xl">
          <div class="col-12 col-md-4">
            <div class="text-h5 text-weight-bold q-mb-md flex items-center">
              <q-icon name="school" class="q-mr-sm" /> ClassMate
            </div>
            <p class="text-grey-4">
              Empowering education through seamless class management and superior learning experiences.
            </p>
          </div>
          <div class="col-6 col-md-2">
            <div class="text-subtitle1 text-weight-bold q-mb-sm">Platform</div>
            <div class="flex column q-gutter-y-xs">
              <span class="cursor-pointer hover-text-accent">Home</span>
              <span class="cursor-pointer hover-text-accent">Features</span>
              <span class="cursor-pointer hover-text-accent">Pricing</span>
            </div>
          </div>
          <div class="col-6 col-md-2">
            <div class="text-subtitle1 text-weight-bold q-mb-sm">Support</div>
            <div class="flex column q-gutter-y-xs">
              <span class="cursor-pointer hover-text-accent">Help Center</span>
              <span class="cursor-pointer hover-text-accent">Contact Us</span>
              <span class="cursor-pointer hover-text-accent">Privacy Policy</span>
            </div>
          </div>
          <div class="col-12 col-md-4">
            <div class="text-subtitle1 text-weight-bold q-mb-sm">Subscribe</div>
            <div class="row no-wrap">
              <q-input dark dense outlined v-model="email" placeholder="Enter your email" class="col" />
              <q-btn color="accent" text-color="dark" label="Join" icon-right="send" class="q-ml-sm" />
            </div>
          </div>
        </div>
        <q-separator dark class="q-my-md" />
        <div class="row justify-between items-center text-grey-5 text-caption">
          <div>© 2024 ClassMate Systems. All rights reserved.</div>
          <div class="q-gutter-x-sm">
            <q-icon name="facebook" size="20px" class="cursor-pointer" />
            <q-icon name="telegram" size="20px" class="cursor-pointer" />
            <q-icon name="message" size="20px" class="cursor-pointer" />
          </div>
        </div>
      </div>
    </q-footer>
  </q-layout>
</template>

<script setup>
import { ref } from 'vue'

const email = ref('')
const mobileMenuOpen = ref(false)

function toggleMobileMenu() {
  mobileMenuOpen.value = !mobileMenuOpen.value
}
</script>

<style scoped>
.container {
  max-width: 1200px;
  margin: 0 auto;
}
.font-heading {
  font-family: 'Inter', sans-serif; /* Setup in SCSS later if needed */
  letter-spacing: -0.5px;
}
.hover-text-accent:hover {
  color: var(--q-accent);
}
</style>
