<template>
  <TheHeader />
  <main>
    <ThePresentation />
    <TheProject />
    <TheContact />
  </main>
  <TheFooter />
</template>

<script setup>
import TheHeader from '@/components/TheHeader.vue'
import TheFooter from '@/components/TheFooter.vue'
import ThePresentation from '@/components/ThePresentation.vue'
import TheProject from '@/components/TheProject.vue'
import TheContact from '@/components/TheContact.vue'
</script>

<style scoped></style>