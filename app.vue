<template>
  <div class="main_container" ref="scrollContainer">
  <div class="section section_home">
    <p>root
    </p>
    <p>food
    </p>
  </div>
    <div class="section">
      <div class="lateral_nav">
      <p>01</p>
      <p>WHY</p>
      </div>
      
      <div class="body_section">
        <img src="" alt="">
      </div>
    </div>
  </div>
</template>
<style>
  .section_home{
    background-image: url('./assets/image/foto_hero.webp') ;
    width: 1920px;
    height: 100vh;
    background-size: cover;
    flex: 0 0 auto;
  }
   .section_home p{
    color: white;
  }
  .main_container{
    display: flex;        /* Rende il contenitore un flex container */
    flex-direction: row;  /* Imposta la direzione dei flex items in orizzontale */
    overflow-x: auto;     /* Abilita lo scorrimento orizzontale se necessario */
    white-space: nowrap;
  }
  .body_section{
    width: 500px;
    flex: 0 0 auto;
  }
</style>
<script>
 export default {
  mounted() {
    // Seleziona il contenitore che deve scorrere orizzontalmente
    const scrollContainer = this.$refs.scrollContainer;

    // Aggiungi event listener allo scroll
    window.addEventListener('wheel', (e) => {
      // Evita lo scroll verticale normale
      e.preventDefault();

      // Modifica lo scrollLeft in base al delta dello scroll verticale
      scrollContainer.scrollLeft += e.deltaY;
    }, { passive: false }); // `passive: false` è necessario per poter chiamare `preventDefault()`
  }
};

</script>