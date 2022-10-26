<script setup>
import Map from '@/components/icons/Map.vue'
</script>

<template>
  <header
    class="min-h-screen flex flex-col justify-evenly items-center relative"
  >
    <div
      class="absolute bg-gradient-to-t inset-0 top-1/3 -bottom-32 from-bkg/80 to-transparent"
    ></div>
    <img
      sizes="(min-width: 500px) 480w, 650w, 800w, 1300w"
      srcset="
        ../assets/images/hero-xs.jpg  480w,
        ../assets/images/hero-sm.jpg  650w,
        ../assets/images/hero-md.jpg  800w,
        ../assets/images/hero-lg.jpg 1300w
      "
      class="absolute h-full w-full object-cover z-0 object-center"
      src="../assets/images/hero.jpg"
      aria-hidden="true"
    />
    <h1
      class="relative text-5xl text-center font-bold text-white tracking-wide py-12 drop-shadow-text-sm lg:drop-shadow-text-lg"
    >
      Unique Trips for<br />
      Adventurous <br />
      Travelers
    </h1>
    <a
      href="#contact-form"
      class="relative bg-accent text-bkg font-medium py-3 px-8 rounded-full borer-bkg focus:outline-none focus-visible:ring-4 ring-accent ring-offset-bkg ring-offset-2 hover:bg-accent/90 flex space-x-2 drop-shadow-text-lg hover:drop-shadow-none transition-shadow"
    >
      <span class="uppercase tracking-wide">Book a Trip</span>
      <Map />
    </a>
  </header>
</template>
