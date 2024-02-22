<script setup>
import AccordationView from './AccordationView.vue';
import { RouterLink } from 'vue-router';
import GalleryView from './GalleryView.vue';
import PartnersView from './PartnersView.vue';


</script>

<template>
    <div class="flex flex-col bg-[#1a332d]">
      <div class="app-container flex justify-center relative mt-24 max-md:gap-6 max-xl:gap-12 gap-24 flex-wrap place-items-center">
        <div class="overlay-box2 max-md:order-2 lg:w-[40%] font-merriweather md:w-[50%] max-md:px-4 max-sm:w-[90%] max-vsm:w-[95%] w-[75%] mb-3">
          <h2 class="overlay-heading2 flex flex-col text-left text-[40px] pb-8 max-sm:pb-4 max-lg:pb-4 max-sm:text-[45px] max-ssm:text-[40px] max-vsm:text-[30px] max-vvsm:text-[30px]">
            <RouterLink to="/team" class="font-extrabold font-montserrat text-[#fbca3f]">The Group</RouterLink>
            <span class="text-[13px] tracking-wide ml-6 -mt-3 text-gray-300 relative font-thin font-merriweather">Click here to view team</span>
          </h2>
          <p class="mb-3 font-montserrat flex justify-center xxl:text[37px] text-[23px] max-sm:text-[23px] max-ssm:text-[21px] max-vsm:text-[21px] ">The RAAGA team is a vibrant and dynamic team dedicated to celebrating the art of music. Comprising passionate individuals from diverse backgrounds, this club fosters creativity and collaboration among its members. With a shared love for melody and rhythm, the team explores various genres and styles, from classical to contemporary, enriching the campus community with their performances and events. Through rehearsals, workshops, and performances, the Music Swara Club not only hones musical skills but also cultivates a sense of camaraderie and mutual appreciation for music's profound impact.</p>
        </div>
        <img class="md:w-[40%] max-md:order-1 max-ssm:w-[85%] w-[70%] saturate-0 bg-blend-color-burn" src="https://i.postimg.cc/cds9hmCR/Whats-App-Image-2024-02-13-at-14-35-28.jpg" alt="temp"/>
      </div>
      <div class="md:pt-24 pt-16">
        <GalleryView />
      </div>
      <div class="home-child"  id="partners-view">
        <!-- <PartnersView ref="homeChild" /> -->
      </div>
      <AccordationView />
    </div>
</template>