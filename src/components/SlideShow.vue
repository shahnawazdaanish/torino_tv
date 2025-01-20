<template>
  <div id="background-slideshow">
    <div class="slideshow-image" v-for="(image, index) in images" :key="index" :style="{ backgroundImage: `url(${image})` }"></div>
  </div>
</template>

<script>
import image1 from '../assets/backgrounds/1.jpg';
import image2 from '../assets/backgrounds/2.jpg';
import image3 from '../assets/backgrounds/3.jpg';
export default {
  name: 'BackgroundSlideshow',
  data() {
    return {
      images: [
        image1,
        image2,
        image3,
      ],
    };
  },
};
</script>

<style scoped>
#background-slideshow {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  z-index: 0; /* Place it behind all content */
  overflow: hidden;
}

.slideshow-image {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-size: cover;
  background-position: center;
  animation: fade 10s infinite;
  opacity: 0;
}

.slideshow-image:nth-child(1) {
  animation-delay: 0s;
}

.slideshow-image:nth-child(2) {
  animation-delay: 5s;
}

.slideshow-image:nth-child(3) {
  animation-delay: 10s;
}

@keyframes fade {
  0%, 100% {
    opacity: 0;
  }
  33%, 66% {
    opacity: 1;
  }
}
</style>
