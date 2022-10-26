<script setup>
import Logo from '@/components/icons/Logo.vue'
import Header from '@/components/Header.vue'
</script>

<template>
  <main
    class="bg-bkg text-white selection:bg-accent selection:text-bkg overflow-hidden"
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
      </section>
    </div>
  </main>
</template>
