<template>
  <div class="main_container" ref="scrollContainer">
  <div class="section section_home">
    <p>root
    </p>
    <p>food
    </p>
  </div>
    <div class="section" data-color="blue">
      <div class="lateral_nav" id="lateral_1">
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
        <div class="title_section">
          <p class="title">WHY</p>
        </div>
        <div class="content_section">
        <div class="upper">
        <p>explore infite potential</p>
        </div>
        <div class="down">
        <p>Rootfood is a personalized Nutritional Advisor and Private Chef Service. <br>
         aimed at helping you explore the infinite possibilities of a delicious,<br> well balanced, carefully evaluated diet.</p>
        </div>
        </div>
      </div>
        

      </div>
    </div>
    <div class="section" data-color="green">
      <div class="lateral_nav_2" id="lateral_2">
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
        <div class="title_section">
          <p class="title">WHY</p>
        </div>
        <div class="content_section">
        <div class="upper">
        <p>explore infite potential</p>
        </div>
        <div class="down">
        <p>Rootfood is a personalized Nutritional Advisor and Private Chef Service. <br>
         aimed at helping you explore the infinite possibilities of a delicious,<br> well balanced, carefully evaluated diet.</p>
        </div>
        </div>
      </div>
        

      </div>
    </div>
  </div>
  <div id="cursor-follower" class="cursor-follower"></div>
</template>
<style>
.content_section{
  padding-top: 200px;
  padding-left: 400px;
  width: 300px;
  .upper{
    padding-bottom: 100px;
  }
  
}
.content_section .down{
  width: 300px;
}
.title_section .title{
  font-size: 200px;
}
.chapter{
  display: flex;
  width: 70%;
  justify-content: space-between;
}
.content{
  width: 900px;
  padding-left: 100px;
  padding-top: 105px;
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
  flex: 0 0 auto;
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
    width: 3000px;
    flex: 0 0 auto;
    display: flex;
  }
  .cursor-follower {
  position: fixed;
  pointer-events: none;
  width: 20px;
  height: 20px;
  border-radius: 50%;
  background-color: red;
  opacity: 0.75; /* Colore iniziale */
  transform: translate(-50%, -50%);
  transition: background-color 0.3s ease, transform 0.1s; 
  z-index: 9999;
}
.fixed_lateral{
  position: fixed;
}

</style>
<script>
 export default {
  data() {
    return {
      counter: 0,
    };
  },
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
    const cursorFollower = document.getElementById('cursor-follower');
    let activeColor = 'red'; // Colore di default

    // Funzione per muovere il pallino
    const moveFollower = (e) => {
      cursorFollower.style.left = `${e.clientX}px`;
      cursorFollower.style.top = `${e.clientY}px`;
    };

    // Aggiungi l'ascoltatore di eventi per il movimento del mouse
    document.addEventListener('mousemove', moveFollower);
    
    
    this.StartInfiniteLoop();
    // Cambia il colore del pallino quando entri in una specifica sezione
    document.querySelectorAll('.section').forEach(section => {
      section.addEventListener('mouseenter', () => {
        console.log('Nuovo colore:', activeColor);
        activeColor = section.getAttribute('data-color');
        cursorFollower.style.backgroundColor = activeColor;
      });
    });
  },
  methods:{
    getPosition(){
      const lateral_1 = document.getElementById('lateral_1')
    const lateral_2 = document.getElementById('lateral_2')
    const rect = lateral_2.getBoundingClientRect();

console.log('Element position: ', rect);
console.log('Top: ', rect.top);
console.log('Right: ', rect.right);
console.log('Bottom: ', rect.bottom);
console.log('Left: ', rect.left);
if(rect.left == 80){
      lateral_1.classList.add('fixed_lateral')
    }
if(rect.left != 80){
  lateral_1.classList.remove('fixed_lateral')
}
    },
    StartInfiniteLoop() {
      const loop = () => {
        this.counter++;
        const lateral_1 = document.getElementById('lateral_1')
    const lateral_2 = document.getElementById('lateral_2')
    const rect = lateral_2.getBoundingClientRect();

console.log('Element position: ', rect);
console.log('Top: ', rect.top);
console.log('Right: ', rect.right);
console.log('Bottom: ', rect.bottom);
console.log('Left: ', rect.left);
if(rect.left == 80){
      lateral_1.classList.add('fixed_lateral')
    }
    if(rect.left != 80){
  lateral_1.classList.remove('fixed_lateral')
}

        setTimeout(loop, 1); // Repeat the loop every 1 second (adjust as needed).
      };

      loop();
    },
    
  }
};

</script>