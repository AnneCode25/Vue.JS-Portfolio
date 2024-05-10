<template>
    <div class="error">
      <h2>404</h2>
  
      <img src="@/assets/images/404.jpg" alt="erreur404" />
    </div>
  </template>
  
  <script setup></script>
  
  <style>
  .error {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }
  
  .error h2 {
    font-size: 100px;
    color: red;
  }
  
  .error img {
    border: 1px solid black;
  }
  </style>