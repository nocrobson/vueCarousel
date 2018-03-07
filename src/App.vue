<template>
  <div id="slider">
    <div class="slide" id="slide01">
      <img src="./assets/01.gif" alt="random 01">
    </div>
    <div class="slide" id="slide02">
      <img src="./assets/02.gif" alt="random 02">
    </div>
    <div class="slide" id="slide03">
      <img src="./assets/03.gif" alt="random 03">
    </div>
    <div class="slide" id="slide04">
      <img src="./assets/04.gif" alt="random 04">
    </div>
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      idCarouselSession:0,
      slideIdPosition:0,
      slideList:['#slide01', '#slide02', '#slide03', '#slide04']
    }
  },
  created(){
    this.iniciarCarousel();
  },
  destroyed() {
    clearInterval(this.idCarouselSession);
  },
  methods:{
    iniciarCarousel() {
      this.idCarouselSession = setInterval(()=>{
        window.location = this.slideList[this.slideIdPosition];
        this.slideIdPosition = this.slideIdPosition >= (this.slideList.length - 1) ? 0 : this.slideIdPosition + 1;
      },3000);
    }
  }
}
</script>

<style>
  .slider {
    width: 100%;
  }

  .slide {
    position: absolute;
    float: left;
    /* display: none; */
    visibility: hidden;
    animation: playCarousel 20S infinite;
    max-width: 100%;
    height: auto;
  }

  .slide:target {
    /* display: block; */
    visibility: visible;
  }



</style>
