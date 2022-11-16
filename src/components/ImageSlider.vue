<script setup>
import { ref, onMounted } from 'vue'
import PrevArrow from '@/components/icons/PrevArrow.vue'
import NextArrow from '@/components/icons/NextArrow.vue'

const sliderInfo = [
  {
    src: new URL('../assets/images/slider-1.jpg', import.meta.url).href,
    alt: 'Iceland Scene',
    text: 'Ocean Wonders',
  },
  {
    src: new URL('../assets/images/slider-2.jpg', import.meta.url).href,
    alt: 'Iceland Scene',
    text: 'Waterfall Cave',
  },
  {
    src: new URL('../assets/images/slider-3.jpg', import.meta.url).href,
    alt: 'Iceland Scene',
    text: 'Rainbow Falls',
  },
  {
    src: new URL('../assets/images/slider-4.jpg', import.meta.url).href,
    alt: 'Iceland Scene',
    text: 'Canyon Peaks',
  },
  {
    src: new URL('../assets/images/slider-5.jpg', import.meta.url).href,
    alt: 'Iceland Scene',
    text: 'Mountain Inlet',
  },
  {
    src: new URL('../assets/images/slider-6.jpg', import.meta.url).href,
    alt: 'Iceland Scene',
    text: 'Angel Cliffs',
  },
  {
    src: new URL('../assets/images/slider-7.jpg', import.meta.url).href,
    alt: 'Iceland Scene',
    text: 'Aurora Sound',
  },
  {
    src: new URL('../assets/images/slider-8.jpg', import.meta.url).href,
    alt: 'Iceland Scene',
    text: 'Icy Meadows',
  },
]

// ImageSlider
const prevBtn = ref()
const nextBtn = ref()
const slideContainer = ref()
const slides = ref([])
let currentIndex = 0
let isMoving = false

// btn handle function
const handleSlideBtnClick = (e) => {
  // TODO: see if slider iss already moving
  if (isMoving) {
    return
  }
  isMoving = true
  e.currentTarget.id === 'prev' ? currentIndex-- : currentIndex++
  console.log(currentIndex)
  slideContainer.value.dispatchEvent(new Event('sliderMove'))
}

// remove/add attribute function
const removeDisabledAttribute = (el) => el.removeAttribute('disabled')
const addDisabledAttribute = (el) => el.setAttribute('disabled', 'true')

// event listeners

onMounted(() => {
  slideContainer.value.addEventListener('sliderMove', () => {
    /**
     * 1. translate the container to the right/left
     * 2. remove disabled attributes
     * 3. enable disabled attribute if needed
     */
    slideContainer.value.style.transform = `translateX(-${
      currentIndex * slides.value[0].clientWidth
    }px)`

    removeDisabledAttribute(prevBtn.value)
    removeDisabledAttribute(nextBtn.value)

    currentIndex === 0 && addDisabledAttribute(prevBtn.value)
  })

  // transition end event
  slideContainer.value.addEventListener(
    'transitionend',
    () => (isMoving = false)
  )

  // disable image drag events
  slides.value.forEach((img) => (img.ondragstart = () => false))

  // intersection observer for slider
  const slideObserver = new IntersectionObserver(
    (slide) => {
      if (slide[0].isIntersecting) {
        addDisabledAttribute(nextBtn.value)
      }
    },
    { threshold: 0.75 }
  )
  slideObserver.observe(slides.value[slides.value.length - 1])
})
</script>

<template>
  <section>
    <div
      aria-labelledby="slider"
      class="container grid gap-4 text-center sm:text-left"
    >
      <div class="relative">
        <div
          class="hidden sm:block absolute w-8 bg-accent/10 -left-4 h-full"
        ></div>
        <div>
          <small
            class="tracking-widest text-accent uppercase drop-shadow-text-sm"
            >Off the Beaten Path</small
          >
          <h2
            id="headline"
            class="text-3xl font-bold tracking-wide drop-shadow-text-md"
          >
            Places without People
          </h2>
        </div>
        <div
          class="flex flex-wrap sm:flex-nowrap justify-center sm:justify-between items-center space-x-4 space-y-4"
        >
          <p class="text-muted max-w-2xl drop-shadow-text-sm">
            We specialize in finding places no one else knows about. Here are a
            few of our favorite spots for true adventurers.
          </p>
          <div class="flex space-x-4">
            <button
              data-slideBtn
              ref="prevBtn"
              id="prev"
              @click="handleSlideBtnClick"
              aria-label="show previous image"
              class="grid place-items-center bg-accent hover:bg-accent/90 rounded-full p-2 text-bkg focus:outline-none focus-visible:ring-4 ring-offset-2 ring-offset-bkg ring-accent disabled:bg-accent/20 disabled:text-accent"
              disabled
            >
              <prev-arrow></prev-arrow>
            </button>
            <button
              data-slideBtn
              ref="nextBtn"
              id="next"
              @click="handleSlideBtnClick"
              aria-label="show next image"
              class="grid place-items-center bg-accent hover:bg-accent/90 rounded-full p-2 text-bkg focus:outline-none focus-visible:ring-4 ring-offset-2 ring-offset-bkg ring-accent disabled:bg-accent/20 disabled:text-accent"
            >
              <next-arrow></next-arrow>
            </button>
          </div>
        </div>
      </div>
    </div>

    <div class="mt-10 sm:mt-20 lg:mt-36 container xs:w-screen">
      <div
        data-slideContainer
        ref="slideContainer"
        class="flex transition-transform duration-500"
      >
        <!-- photos -->
        <div
          data-slide
          class="relative w-full xs:w-auto flex-grow flex-shrink-0 xs:basis-96 pr-4"
          ref="slides"
          v-for="(slide, index) in sliderInfo"
          :key="index"
        >
          <img
            :src="slide.src"
            :alt="slide.alt"
            class="object-cover h-full [@media(hover:hover)]:grayscale hover:grayscale-0 transition-all peer"
          />
          <p
            class="absolute bottom-4 left-4 px-4 py-2 bg-bkg font-bold text-lg pointer-events-none tracking-wide [@media(hover:hover)]:opacity-0 peer-hover:opacity-100 transition-opacity"
          >
            {{ slide.text }}
          </p>
        </div>
      </div>
    </div>
  </section>
</template>
