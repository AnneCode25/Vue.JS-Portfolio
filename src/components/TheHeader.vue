<template>
    <header>
      <figure class="logo">
        <RouterLink to="/">
          <img src="@/assets/images/AV.svg.png" alt="logo" @click="scrollToTop" />
        </RouterLink>
      </figure>
      <h1>Portfolio - Développeuse Web Junior</h1>
      <nav id="nav">
        <ul>
          <li
            v-for="(title, index) in titles"
            :key="index"
            :class="{ active: activeIndex === index }"
            @click="updateActive(index)"
          >
            <a :href="title.href">{{ title.label }}</a>
          </li>
        </ul>
      </nav>
    </header>
  </template>
  
  <script setup lang="ts">

  //Fonction pour revenir en haut de la page lors du clic sur le logo
  const scrollToTop = () => {
    window.scrollTo({
      top: 0,
      behavior: 'smooth'
    })
  }
  
  //Création du tablea du menu ancrée + lien actif pour souligné l'élément actif dans le menu

  import { ref } from 'vue'
  
  const titles = [
    { label: 'Présentation', href: '#presentation' },
    { label: 'Créations', href: '#projects' },
    { label: 'Contact', href: '#formulaire' }
  ]
  
  const activeIndex = ref(0)
  
  const updateActive = (index) => {
    activeIndex.value = index
  }
  </script>
  
  <style scoped>
  header {
    font-size: 80%;
    font-family: Bogart;
    background-color: cadetblue;
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    align-items: center;
    padding: 0;
    margin: 0;
    flex: 0 1 70%;
    position: fixed;
    top: 0;
    width: 100%;
    z-index: 1000;
  }
  
  header nav ul li a.active {
    text-decoration: underline;
  }
  
  header nav {
    /* background-color: violet; */
    flex: 0 1 30%;
  }
  
  header nav ul {
    padding: 0;
    display: flex;
    flex-direction: row;
    justify-content: space-around;
    list-style: none;
    align-items: center;
  }
  
  header nav ul a {
    font-size: 150%;
    color: black;
    text-decoration: none;
  }
  
  header figure {
    width: 80px;
    height: 80px;
    margin: 0px;
    padding: 5px;
  }
  
  header figure img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    border-radius: 50%;
    object-position: left;
    box-shadow: 0 0 30px lightblue;
  }
  
  .active {
    text-decoration: underline;
  }
  </style>
  