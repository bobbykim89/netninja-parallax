<script setup>
import { ref, onMounted, computed } from 'vue'
import PaperPlane from '@/components/icons/PaperPlane.vue'
import Loading from '@/components/icons/Loading.vue'

// btn text
let btnText = 'signup'
// form handle
const contactForm = ref()
const contactBtn = ref()
const contactInput = ref()
const inputValue = ref('')

const addDisabledAttribute = (el) => el.setAttribute('disabled', 'true')

// fake sending email to api endpoint
const postEmailToDB = (email) => {
  console.info(`Your email is ${email}`)
  return new Promise((resolve) => setTimeout(resolve, 2000))
}

// options for submit button
const contactBtnOptions = {
  pending: `
    <svg xmlns="http://www.w3.org/2000/svg" class="animate-spin" width="24" height="24" fill="currentColor" viewBox="0 0 256 256"><rect width="256" height="256" fill="none"></rect><line x1="128" y1="32" x2="128" y2="64" fill="none" stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="24"></line><line x1="224" y1="128" x2="192" y2="128" fill="none" stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="24"></line><line x1="195.9" y1="195.9" x2="173.3" y2="173.3" fill="none" stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="24"></line><line x1="128" y1="224" x2="128" y2="192" fill="none" stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="24"></line><line x1="60.1" y1="195.9" x2="82.7" y2="173.3" fill="none" stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="24"></line><line x1="32" y1="128" x2="64" y2="128" fill="none" stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="24"></line><line x1="60.1" y1="60.1" x2="82.7" y2="82.7" fill="none" stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="24"></line></svg>
    <span class="uppercase tracking-wide animate-pulse">
    Sending...
    </span>
    `,
  success: `
  <span class="uppercase tracking-wide">
    Thank you!
    </span>
    <span class="uppercase tracking-wide">
    ✌️
    </span>
  `,
}

const buttonText = computed(() => btnText)

const handleFormSubmit = async (e) => {
  //   e.preventDefault()
  console.log('prevented')
  addDisabledAttribute(contactForm.value)
  addDisabledAttribute(contactBtn.value)
  btnText = 'pending'
  contactBtn.value.innerHTML = contactBtnOptions.pending
  const userEmail = inputValue.value
  contactInput.value.style.display = 'none'
  await postEmailToDB(userEmail)
  btnText = 'success'
  contactBtn.value.innerHTML = contactBtnOptions.success
}

onMounted(() => {
  // contactForm.addEventListener('submit', handleFormSubmit)
})
</script>

<template>
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
          ref="contactForm"
          @submit.prevent="handleFormSubmit"
        >
          <input
            type="email"
            required
            placeholder="Email Address"
            id="email"
            class="p-2 mx-4 bg-transparent w-full text-sm flex-1 border-b-2 border-transparent rounded-none caret-accent placeholder:text-white focus:placeholder:text-muted focus:outline-none focus:border-accent"
            ref="contactInput"
            v-model="inputValue"
          />
          <label for="email" class="sr-only">Enter your email address</label>
          <button
            class="bg-accent text-bkg font-medium text-sm py-3 px-4 sm:px-8 rounded-full border border-bkg focus:outline-none focus-visible:ring-4 ring-accent ring-offset-bkg ring-offset-2 hover:bg-accent/90 flex space-x-2 shrink-0"
            id="contact-btn"
            ref="contactBtn"
          >
            <div v-if="buttonText === 'signup'" class="flex space-x-2 shrink-0">
              <span class="uppercase tracking-wide">Sign Up</span>
              <paper-plane />
            </div>
            <div
              v-if="buttonText === 'pending'"
              class="flex space-x-2 shrink-0"
            >
              <loading></loading>
              <span class="uppercase tracking-wide animate-pulse">
                Sending...
              </span>
            </div>
            <div
              v-if="buttonText === 'success'"
              class="flex space-x-2 shrink-0"
            >
              <span class="uppercase tracking-wide"> Thank you! </span>
              <span class="uppercase tracking-wide"> ✌️ </span>
            </div>
          </button>
        </form>
      </div>
    </div>
  </section>
</template>
