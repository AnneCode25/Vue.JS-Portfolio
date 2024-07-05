<template>
  <div v-if="isModalOpen" class="modal-overlay" @click="closeModal">
    <div class="modal" @click.stop>
      <div class="Section1">
        <button @click="closeModal">X</button>
        <h2>{{ creation?.name }}</h2>
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
      <p><strong>Desription: </strong>{{ creation?.description }}</p>
      <p><strong>Technologies utilisées: </strong>{{ creation?.technologies.join(', ') }}</p>
      <p><strong>Date de création: </strong>{{ creation?.dateCreation }}</p>
      <p>
        <strong>Lien Github: </strong>
        <a :href="creation.lienGithub" target="_blank">{{ creation?.lienGithub }}</a>
      </p>
      <p>
        <strong>Lien site internet/ Pdf: </strong>
        <a :href="creation.pageInternet" target="_blank">{{ creation?.pageInternet }}</a>
      </p>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import { computed } from 'vue'
import { watch } from 'vue'

const props = defineProps({
  isModalOpen: Boolean,
  creation: Object
})

const emit = defineEmits(['close'])

const closeModal = () => {
  emit('close')
}

const currentImageIndex = ref(0)

const previousImage = () => {
  currentImageIndex.value =
    (currentImageIndex.value - 1 + props.creation?.images?.length || 1) %
    (props.creation?.images?.length || 1)
}

const nextImage = () => {
  currentImageIndex.value = (currentImageIndex.value + 1) % (props.creation?.images?.length || 1)
}

const currentImageSrc = computed(() => {
  return props.creation?.images[currentImageIndex.value] || ''
})

watch(
  () => props.isModalOpen,
  () => {
    if (props.isModalOpen) {
      currentImageIndex.value = 0
    }
  }
)
</script>

<style scoped>
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
