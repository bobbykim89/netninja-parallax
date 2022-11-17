<script setup>
import LogoColor from './icons/LogoColor.vue'

const aboutText = ['About Us', 'Press', 'News']
const locationText = [
  'Africa',
  'Australia',
  'Europe',
  'North America',
  'South America',
]
const contactText = ['Email', 'Instagram', 'Facebook', 'Twitter']
</script>

<template>
  <footer
    class="border-t border-accent mt-16 sm:mt-24 lg:mt-40 py-6 sm:py-8 md:py-12"
  >
    <div
      class="container flex flex-wrap md:justify-between items-center md:items-start gap-12"
    >
      <div
        class="grid gap-2 justify-items-center md:justify-items-start basis-full md:basis-1/4"
      >
        <logo-color></logo-color>
        <p class="text-muted text-sm text-center md:text-left">
          We curate unique experiences <br />for the adventurous traveler.
        </p>
      </div>
      <nav
        aria-label="Secondary navigation"
        class="text-sm flex flex-col items-center sm:items-start sm:flex-row text-center sm:text-left gap-6 justify-between md:justify-around grow md:basis-1/2 mt-2"
      >
        <div class="grid gap-3">
          <p
            class="font-bold underline decoration-accent decoration-4 underline-offset-2 tracking-wide px-4"
          >
            About
          </p>
          <ul aria-label="About Traverse">
            <li v-for="(item, i) in aboutText" :key="i">
              <a
                href="#"
                class="hover:text-accent transition-colors focus:outline-none focus-visible:ring-4 ring-offset-2 ring-offset-bkg px-4 ring-accent rounded-full"
                >{{ item }}</a
              >
            </li>
          </ul>
        </div>
        <div class="grid gap-3">
          <p
            class="font-bold underline decoration-accent decoration-4 underline-offset-2 tracking-wide px-4"
          >
            Locations
          </p>
          <ul aria-label="About Traverse">
            <li v-for="(item, i) in locationText" :key="i">
              <a
                href="#"
                class="hover:text-accent transition-colors focus:outline-none focus-visible:ring-4 ring-offset-2 ring-offset-bkg px-4 ring-accent rounded-full"
                >{{ item }}</a
              >
            </li>
          </ul>
        </div>
        <div class="grid gap-3">
          <p
            class="font-bold underline decoration-accent decoration-4 underline-offset-2 tracking-wide px-4"
          >
            Contact Us
          </p>
          <ul aria-label="About Traverse">
            <li v-for="(item, i) in contactText" :key="i">
              <a
                href="#"
                class="hover:text-accent transition-colors focus:outline-none focus-visible:ring-4 ring-offset-2 ring-offset-bkg px-4 ring-accent rounded-full"
                >{{ item }}</a
              >
            </li>
          </ul>
        </div>
      </nav>
    </div>
  </footer>
</template>
