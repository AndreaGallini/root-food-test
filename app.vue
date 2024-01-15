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
      <div  class="hero_img ">
        <img src="./assets/image/riso_why.png" alt="">
      </div>
      <div class="content">
        <section class="chapter">
          <p>chapter</p>
          <p>001</p>
          <p>one</p>
        </section>
      </div>
        

      </div>
    </div>
  </div>
</template>
<style>
.chapter{
  display: flex;
  width: 70%;
  justify-content: space-between;
}
.content{
  width: 900px;
  padding-left: 100px;
  padding-top: 150px;
}
.hero_img{
  position: relative;
  background-image: url('./assets/image/foto_why_1.png') ;
  width: 900px;
  height: 100vh;
  background-size: cover;
}
.hero_img img{
    position: absolute;
    bottom: 0;
    left: 600px;
    width: 600px;
}
.section{
  display: flex;
}
.lateral_nav{
  border: 1px solid black
}
  .section_home{
    background-image: url('./assets/image/foto_hero.webp') ;
    width: calc(100% - 80px);
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
    width: 1900px;
    flex: 0 0 auto;
    display: flex;
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