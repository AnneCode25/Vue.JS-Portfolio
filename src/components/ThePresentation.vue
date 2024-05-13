<template>
  <section id="presentation">
    <figure>
      <img src="@/assets/images/photo.jpg" alt="Photo de profil">
    </figure>
    <div>
      <h2>Présentation</h2>
      <p>
        Forte d'une solide expérience dans le domaine de la comptabilité, je suis actuellement en
        transition vers une carrière dans le développement informatique. Mon parcours professionnel
        m'a permis de développer une expertise pointue dans la gestion précise des données, la
        résolution de problèmes complexes et la collaboration interfonctionnelle. En tant que
        comptable, j'ai acquis une sensibilité particulière à l'importance de l'exactitude et de la
        fiabilité des informations, des compétences qui sont tout aussi cruciales dans le
        développement logiciel.
      </p>
      <p>
        Passionnée par la technologie et son potentiel pour résoudre des défis complexes, je suis
        animée par la volonté d'appliquer mes compétences comptables au monde du développement. Je
        suis convaincue que cette fusion entre mon expérience comptable et mon intérêt pour la
        programmation peut donner naissance à des solutions innovantes et efficaces.
      </p>
      <p>
        Mon approche méthodique, forgée par des années de travail dans le domaine financier, me
        permet d'aborder la programmation avec rigueur et précision. Je suis déterminé(e) à tirer
        parti de cette expérience pour contribuer de manière significative à des projets de
        développement, en mettant en avant la création de solutions robustes et orientées vers les
        besoins réels des utilisateurs.
      </p>
      <p>
        Cette transition représente pour moi bien plus qu'un simple changement de carrière ; c'est
        l'occasion de combiner mes compétences existantes avec ma passion grandissante pour la
        technologie, afin de m'engager dans un domaine en constante évolution où je pourrai
        continuer à apprendre et à évoluer en tant que professionnel
      </p>
    </div>
  </section>
</template>

<style scoped>
section {
  display: flex;
  flex-direction: row;
  justify-content: space-around;
  align-items: center;
  border-bottom: 2px solid cadetblue;
}

section figure {
  width: 960px;
  height: 540px;
  flex: 1;
  max-width: calc(100% / 4);
}

section figure img {
  width: 100%;
  height: 100%;
  object-fit: contain;
  filter: grayscale(100%);
}

section div {
  text-align: justify;
  flex: 1;
}
</style>
