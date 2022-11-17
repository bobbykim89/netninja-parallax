<script setup>
import { ref, onMounted } from 'vue'
import Logo from '@/components/icons/Logo.vue'
import Header from '@/components/Header.vue'
import FooterComponent from '@/components/FooterComponent.vue'
import ImageSlider from '@/components/ImageSlider.vue'
import PaperPlane from '@/components/icons/PaperPlane.vue'
</script>

<template>
  <main
    class="bg-bkg text-base text-white selection:bg-accent selection:text-bkg overflow-hidden"
  >
    <div id="parallax">
      <nav
        class="grid place-items-center absolute w-full top-0 z-50 drop-shadow-text-sm"
        aria-label="Primary Navigation"
      >
        <a
          href="/"
          aria-label="Go Home"
          class="p-1 m-4 focus:outline-none focus-visible:ring-4 ring-accent rounded-full transition-shadow"
        >
          <logo />
        </a>
      </nav>
      <Header />
      <section
        class="relative mt-16 sm:mt-24 lg:mt-40 pb-16 -mb-16 grid gap-16 sm:gap-24 lg:gap-40 overflow-hidden"
      >
        <div
          aria-labelledby="headline"
          class="container grid gap-4 text-center max-w-prose"
        >
          <div>
            <small
              class="tracking-widest text-accent uppercase drop-shadow-text-sm"
              >WHAT DREAMS ARE MADE OF</small
            >
            <h2
              id="headline"
              class="text-3xl font-bold tracking-wide drop-shadow-text-md"
            >
              Trips for Explorers
            </h2>
            <p class="text-muted drop-shadow-text-sm">
              We find once-in-a-lifetime locations and reserve them for
              travelers full of adventure. Calling all explorers and extremists
              to the trip of their dreams in the most exotic locations all
              around the globe.
            </p>
          </div>
        </div>
        <!-- slider-component -->
        <image-slider></image-slider>
        <section
          aria-labelledby="map"
          class="container flex flex-wrap md:space-x-16 space-y-12 md:space-y-0 justify-between items-center"
        >
          <img
            src="../assets/images/map.png"
            alt="Map"
            width="400"
            class="grow md:flex-1"
            loading="lazy"
          />
          <div class="grid gap-4 text-center md:text-left grow md:flex-1">
            <div class="relative">
              <div
                class="hidden md:block absolute w-8 bg-accent/10 -left-4 h-full"
              ></div>
              <small class="tracking-widest text-accent uppercase"
                >A globe of possibilities</small
              >
              <h2 id="map" class="text-3xl font-bold tracking-wide">
                Happy Travelers <br />
                the World Over
              </h2>
              <p class="text-muted max-w-2xl">
                Don’t take our word for it! Thousands of adventurous travelers
                have enjoyed more than 250 exotic locations all over the globe!
              </p>
            </div>
          </div>
        </section>
        <section
          aria-labelledby="map"
          class="container grid gap-4 text-center max-w-prose"
        >
          <div class="grid gap-4 text-center md:text-left grow md:flex-1">
            <div>
              <small class="tracking-widest text-accent uppercase"
                >It’s Time to Explore</small
              >
              <h2 id="cta" class="text-3xl font-bold tracking-wide">
                Get Hidden Locations
              </h2>
              <p class="text-muted max-w-2xl mx-auto">
                Not sure where to start? Drop us a line, and we’ll send you new
                locations before they’re shown on our website.
              </p>
              <form
                id="contact-form"
                class="border-4 border-accent rounded-full p-1 flex items-center justify-between max-w-md mx-auto"
              >
                <input
                  type="email"
                  required
                  placeholder="Email Address"
                  id="email"
                  class="p-2 mx-4 bg-transparent w-full text-sm flex-1 border-b-2 border-transparent rounded-none caret-accent placeholder:text-white focus:placeholder:text-muted focus:outline-none focus:border-accent"
                />
                <label for="email" class="sr-only"
                  >Enter your email address</label
                >
                <button
                  class="bg-accent text-bkg font-medium text-sm py-3 px-4 sm:px-8 rounded-full border border-bkg focus:outline-none focus-visible:ring-4 ring-accent ring-offset-bkg ring-offset-2 hover:bg-accent/90 flex space-x-2 shrink-0"
                  id="contact-btn"
                >
                  <span class="uppercase tracking-wide">Sign Up</span>
                  <paper-plane />
                </button>
              </form>
            </div>
          </div>
        </section>
      </section>
      <footer-component></footer-component>
    </div>
  </main>
</template>
