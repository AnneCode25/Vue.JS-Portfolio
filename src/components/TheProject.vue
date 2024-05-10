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
    <div v-if="isModalOpen" class="modal-overlay" @click="closeModal">
      <div class="modal" @click.stop>
        <div class="Section1">
          <button @click="closeModal">X</button>
          <h2>{{ selectedCreation.name }}</h2>
        </div>
        <div class="Section2">
          <button @click="previousImage">
            <img src="@/assets/images/fleche_gauche.png" alt="fleche gauche" />
          </button>
          <figure>
            <img :src="currentImageSrc" alt="Image" />
          </figure>
          <button @click="nextImage">
            <img src="@/assets/images/fleche_droite.png" alt="fleche droite" />
          </button>
        </div>
        <p><strong>Desription: </strong>{{ selectedCreation.description }}</p>
        <p>
          <strong>Technologies utilisées: </strong>{{ selectedCreation.technologies.join(', ') }}
        </p>
        <p><strong>Date de création: </strong>{{ selectedCreation.dateCreation }}</p>
        <p>
          <strong>Lien Github: </strong>
          <a :href="selectedCreation.lienGithub" target="_blank">{{
            selectedCreation.lienGithub
          }}</a>
        </p>
        <p>
          <strong>Lien site internet/ Pdf: </strong>
          <a :href="selectedCreation.pageInternet" target="_blank">{{
            selectedCreation.pageInternet
          }}</a>
        </p>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">

//Import du tableau de données concernants les créations
import sourceData from '@/creations.json'

const creations = sourceData.creations

// Fonction pour ouvrir le modal et afficher la création sélectionnée
import { ref } from 'vue'
import { computed } from 'vue'
import { onMounted } from 'vue'

const isModalOpen = ref(false)
const selectedCreation = ref(null)

const openModal = (creation) => {
  selectedCreation.value = creation
  isModalOpen.value = true
}

const closeModal = () => {
  isModalOpen.value = false
}

selectedCreation.value = sourceData.creations[0]
const currentImageIndex = ref(0)

const previousImage = () => {
  currentImageIndex.value =
    (currentImageIndex.value - 1 + selectedCreation.value.images.length) %
    selectedCreation.value.images.length
}

const nextImage = () => {
  currentImageIndex.value = (currentImageIndex.value + 1) % selectedCreation.value.images.length
}

const currentImageSrc = computed(() => {
  return selectedCreation.value.images[currentImageIndex.value]
})

onMounted(() => {
  window.scrollTo({ top: 0, behavior: 'smooth' })
})
</script>


<style scoped>
section {
  display: flex;
  background-color: rgba(95, 158, 160, 0.494);
  flex-direction: column;
  border-bottom: 2px solid cadetblue;
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

.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 1000;
}

.modal {
  background-color: cadetblue;
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.5);
  width: 960px;
  height: 600px;
  margin-top: 50px;
  margin-bottom: 50px;
  display: flex;
  flex-direction: column;
  overflow: auto;
  align-content: center;
  justify-content: space-around;
  overflow: auto;
}

.modal .Section1 {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  height: 50px;
}

.modal .Section1 button {
  display: flex;
  flex: 1 1 1%;
  background: none;
  border: none;
}

.modal .Section1 h2 {
  display: flex;
  flex: 1 1 99%;
}

.modal .Section2 {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  flex: 1;
  flex: 1 1 80%;
  height: 300px;
  margin: 5px 0px;
}

.modal .Section2 button {
  height: 300px;
  display: flex;
  align-items: center;
}

.modal .Section2 button img {
  width: 20px;
  height: 20px;
}

.modal .Section2 figure {
  width: 960px;
  height: 300px;
}

.modal .Section2 figure img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: top;
}

.modal p {
  height: 50px;
  margin: 0px;
}
</style>
