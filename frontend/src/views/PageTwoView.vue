<script setup>
import Page2Video from '../assets/video/Page2Video.mp4';
import { ref, onMounted } from 'vue';

const bgVideo2 = ref(null);

onMounted(() => {
      if (bgVideo2.value) {
        bgVideo2.value.play().catch(error => {
          console.error('Autoplay failed:', error);
        });
      }
    })
</script>

<template>
    <div class="app-container relative justify-start max-ssm:px-8 max-md:justify-center max-xl:justify-end flex place-items-center m-0 overflow-hidden">
      <video ref="bgVideo2" class="object-cover" muted loop autoplay width="100%" height="100vh" :style="{ opacity: '0.5' }">
        <source :src="Page2Video" type="video/mp4">
      </video>
      <div class="overlay-box md:mx-16">
        <h2 class="overlay-heading font-extrabold mb-3 text-[40px] max-md:text-[35px] max-sm:text-[30px] max-ssm:text-[25px]">Raaga' 24</h2>
        <p class="text-[17px] font-montserrat max-sm:text-[16px] max-ssm:text-[14px] mb-3 ">RAAGA is a national level music festival organized by SWARA, the official music club of K L University. The music festival consists of several competitions, spot events and expos to celebrate music in different ways and to encourage people to participate in areas of their liking, symbolising that music is for everyone.<br><br>
          <p class="text-[17px] font-montserrat max-sm:text-[16px] font-semibold max-ssm:text-[14px] mb-3 ">Raaga is a music festival with a variety of events, competitions and workshops that has a potential to make people of different interests and backgrounds to feel engaged and explore aspects of music
          </p>
        </p>
      </div>
    </div>


</template>

<style scoped>
.app-container {
  height: 100vh;
  background-color: #1a332d;
}

.overlay-box {
  max-width: 500px;
  background-color: transparent;
  backdrop-filter: blur(25px);
  box-shadow: 0 0 10 rgba(0, 0, 0, .5);
  padding: 20px;
  border-radius: 10px;
  text-align: left;
  color: #fff;
}

.overlay-box p {
  letter-spacing: 1px;
}

.overlay-heading {
  font-family: 'Merriweather', serif;
}


video {
  object-fit: fill;
  position: absolute;
  height: 100%;
}

.content-container {
  text-align: center;
  padding: 20px;
  background-color: #000;
}

</style>
