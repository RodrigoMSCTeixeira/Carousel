<template>
  <div class="gallery">
    <div v-for="image in galleries" :key="image.name" class="gallery-section">
      <div v-if="image.category == false">
        <h2 class="gallery-title">{{ image.title }}</h2>
        <Swiper :options="swiperOptions">
          <SwiperSlide v-for="slide in image.images" :key="slide">
            <img :src="slide" alt="Carousel image" />
          </SwiperSlide>
        </Swiper>
      </div>
      <div v-else></div>
    </div>
  </div>
</template>

<script>
import { Swiper, SwiperSlide, directive } from 'vue-awesome-swiper'
import 'swiper/css/swiper.css'

export default {
  name: 'Carousel',
  components: {
    Swiper,
    SwiperSlide
  },
  directives: {
    swiper: directive
  },

  data() {
    return {
      swiperOptions: {
        effect: 'coverflow',
        grabCursor: true,
        centeredSlides: true,
        slidesPerView: 2,
        coverflowEffect: {
          rotate: 0,
          stretch: 0,
          depth: 400,
          modifier: 6,
          slideShadows: false
        },
        pagination: true,
        modules: 'modules',
        loop: true,
        autoplay: {
          delay: 2000,
          disableOnInteraction: true
        }
      },
      galleries: [
        {
          name: 'CodeHall Carousel using nuxt',
          category: false,
          title: 'Carousel Using Nuxt',
          images: {
            photo01: 'https://swiperjs.com/demos/images/nature-1.jpg',
            photo02: 'https://swiperjs.com/demos/images/nature-2.jpg',
            photo03: 'https://swiperjs.com/demos/images/nature-3.jpg',
            photo04: 'https://swiperjs.com/demos/images/nature-4.jpg',
            photo05: 'https://swiperjs.com/demos/images/nature-5.jpg',
            photo06: 'https://swiperjs.com/demos/images/nature-6.jpg'
          }
        }
      ]
    }
  }
}
</script>

<style lang="css">
@import '~/static/css/carousel.css';
</style>
