<template>
  <section id="projects">
    <h2>Mes créations</h2>
    <div class="creations">
      <div
        class="div"
        v-for="creation in creations"
        :key="creation.id"
        @click="openModal(creation)"
      >
        <h3>{{ creation.name }}</h3>
        <figure>
          <img :src="`/public/images/${creation.image}`" :alt="creation.name" />
        </figure>
      </div>
    </div>
    <TheModal :isModalOpen="isModalOpen" :creation="selectedCreation" @close="closeModal" />
  </section>
</template>

<script setup lang="ts">
//Import du tableau de données concernants les créations
import TheModal from './TheModal.vue'
import sourceData from '@/creations.json'
import { ref } from 'vue'

const creations = sourceData.creations
const isModalOpen = ref(false)
const selectedCreation = ref(null)

const openModal = (creation) => {
  selectedCreation.value = creation
  isModalOpen.value = true
}

const closeModal = () => {
  isModalOpen.value = false
}
</script>

<style scoped>
section {
  display: flex;
  flex-direction: column;
}

section h2 {
  display: flex;
  justify-content: center;
}

.creations {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: center;
}

.creations h3 {
  display: flex;
  justify-content: center;
}

.creations figure {
  width: 640px;
  height: 360px;
}

.creations img {
  object-position: top;
  object-fit: cover;
  width: 100%;
  height: 100%;
}

.div:hover {
  box-shadow: 10px 10px 15px cadetblue;
}
</style>
