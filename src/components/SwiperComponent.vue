<template>
    <section class="swiper-slider">
      <div class="slider">
        <img :src="images[activeSlide].src"/>
        <button @click="nextSlide" class="precedent">&lt;</button>
        <button @click="prevSlide" class="suivant">&gt;</button>
      </div>
    </section>
  </template>
  
  <script>

  export default {
    data() {
      return {
        activeSlide: 0,
        images: [
          {
            id: 1,
            src: "../assets/image1.jpg",
          },
          {
            id: 2,
            src: "../assets/image2.jpg"
          },
          {
            id: 3,
            src: "../assets/image3.jpg"
          },
          {
            id: 4,
            src: "../assets/image4.jpg"
          },
          {
            id: 5,
            src: "../assets/image5.jpg"
          },
          {
            id: 6,
            src: "../assets/image6.jpg"
          }
        ],
        timer:0,
      }
    },
    mounted: function(){
      this.startSlide()
    },
    methods: {
      nextSlide() {
        if (this.activeSlide < this.images.length - 1) {
          this.activeSlide++
        } else {
          this.activeSlide = 0
        }
      },
      prevSlide() {
        if (this.activeSlide !== 0) {
          this.activeSlide--
        } else {
          this.activeSlide = this.images.length - 1
        }
      },
      startSlide: function(){
        this.timer = setInterval(this.nextSlide, 3000)

      }
    },
  }
  </script>
  
  <style scoped>
  .swiper-slider {
    width:800px;
    height: 500px;
    border-radius: 10px;
    overflow: hidden;
    margin: auto;
    position: relative;

  
   
  }

  
  .slider img {
    overflow: hidden;
    width:800px;
    height: 500px;
    position: absolute;
    top: 0;
    left: 0;
    margin: auto;
    object-fit: cover;

  }
  
  .precedent, .suivant {
    position: absolute;
    font-size: 50px;
    top: 250px;
    cursor: pointer;
  }
  
  .precedent {
    left: 0;
  }
  
  .suivant {
    right: 0;
  }
  @media screen and (max-width: 768px) {
    .swiper-slider{
      margin: 5rem;
    }
    
 
  }
  </style>
  