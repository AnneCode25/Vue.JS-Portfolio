<template>
    <footer>
      <div>
        <a href="https://github.com/nnannou" target="_blank">
          <img src="@/assets/images/Github.png" alt="Logo Github" />
        </a>
        <a href="https://fr.linkedin.com/" target="_blank"
          ><img src="@/assets/images/Linkedin.png" alt="Logo Linkedin"
        /></a>
        <a href="https://twitter.com/?lang=fr" target="_blank"
          ><img src="@/assets/images/twitter.png" alt="Logo Twitter"
        /></a>
      </div>
      <div>
        <p><small>&copy; Anne Villette. Tous droit réservés.</small></p>
        <p>
          <small>Dernière mise à jour : <time datetime="2024-05-10"> 10 mai 2024</time></small>
        </p>
      </div>
    </footer>
  </template>
  
  <style scoped>
  footer {
    background-color: rgba(95, 158, 160, 0.494);
    display: flex;
    flex-direction: row;
    padding: 10px;
    justify-content: space-between;
    align-items: center;
  }
  
  footer div {
    display: flex;
    flex-direction: row;
  }
  
  footer img {
    width: 35px;
    height: 35px;
    margin: 5px;
  }
  
  footer div:last-of-type {
    display: flex;
    flex-direction: column;
  }
  
  footer p {
    margin: 5px;
    font-size: 80%;
  }
  </style>
  