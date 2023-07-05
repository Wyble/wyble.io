<script setup lang="ts">
import gsap from 'gsap'
import ScrollTrigger from 'gsap/ScrollTrigger'
import { onMounted, ref } from 'vue'

// create stars
const colors = [
  // 'bg-violet-600',
  // 'bg-orange-600',
  'bg-red-600',
  // 'bg-green-600',
  'bg-blue-600',
  'bg-white',
  'bg-white',
  'bg-white'
]
const blurs = ['blur-[1px]', 'blur-[2px]', 'blur-[3px]']

function createStar() {
  const star = {
    x: Math.floor(Math.random() * 100) + '%',
    y: Math.floor(Math.random() * 60 + 20) + '%',
    blur: blurs[Math.floor(Math.random() * blurs.length)],
    color: colors[Math.floor(Math.random() * colors.length)]
  }

  return star
}

let stars = Array.from({ length: Math.floor(Math.random() * 20 + 10) }, createStar)

// animate the stars
const heroSection = ref<HTMLDivElement | null>(null)
onMounted(() => {
  gsap.registerPlugin(ScrollTrigger)
  const starsElements = gsap.utils.toArray<HTMLDivElement>('.star')

  starsElements.forEach((star) => {
    gsap.to(star, {
      scrollTrigger: {
        trigger: heroSection.value,
        toggleActions: 'play pause resume none'
      },
      '--x': '-10%',
      '--y': 'random(100, 0)',
      duration: () => Math.random() * 20 + 5,
      repeat: Infinity,
      onComplete() {
        star.style.setProperty('--x', '100%')
        star.style.setProperty('--y', Math.floor(Math.random() * 60 + 20) + '%')
      }
    })
  })
})
</script>

<template>
  <section ref="heroSection" class="mb-52 lg:mb-56">
    <div class="relative flex items-center justify-center pt-32 mx-4 md:mx-6 md:pt-64 xl:mx-auto">
      <!-- hero content -->
      <div class="max-w-5xl mx-auto text-center">
        <h1
          class="mb-4 text-4xl font-heading leading-relaxed text-transparent bg-gradient-to-r from-violet-600 to-amber-600 bg-clip-text md:text-6xl md:leading-normal"
        >
          Unleash the Power of Wyble Elevate Your Digital Presence
        </h1>
        <p class="mb-8 text-lg leading-loose tracking-wider md:text-2xl">
          Unlock Your Digital Potential with Comprehensive Solutions - Web, Mobile, and Desktop
          Development Expertise Combined with Captivating Filmmaking Services
        </p>

        <div class="max-w-xs mx-auto sm:flex sm:max-w-none sm:justify-center sm:gap-4">
          <div class="">
            <button
              class="font-medium border-transparent border rounded-sm inline-flex justify-center items-center px-8 py-3 w-full mb-4 bg-violet-700 hover:bg-violet-400 text-white transition-colors duration-300"
            >
              Get In Touch
            </button>
          </div>
          <div class="">
            <button
              class="font-medium border-transparent border rounded-sm inline-flex justify-center items-center px-8 py-3 w-full mb-4 bg-neutral-800 hover:bg-neutral-500 text-white transition-colors duration-300"
            >
              Learn More
            </button>
          </div>
        </div>
      </div>

      <!-- blur -->
      <div class="relative opacity-50 -translate-x-96 -translate-y-52 blur-3xl -z-10">
        <div
          class="absolute rounded-full right-44 h-96 w-96 bg-gradient-to-t from-violet-400 to-pink-600"
        ></div>
        <img
          class="absolute max-w-none w-[700px] top-0 right-0 blur-3xl"
          src="/Pmmvryu8f044FKI424PTTRBEs.png"
        />
        <!-- <div class="absolute rounded-full right-1 h-96 w-96 bg-gradient-to-t from-violet-500 to-pink-700"></div> -->
      </div>

      <!-- stars -->
    </div>
    <div class="absolute top-0 left-0 -z-50 w-full h-full">
      <div
        v-for="(star, i) in stars"
        :key="i"
        class="absolute w-1 h-1 rounded-full star"
        :class="`${star.color} ${star.blur}`"
        :style="`--x:${star.x};--y:${star.y}`"
      ></div>
    </div>
  </section>
</template>
<style scoped>
.star {
  left: var(--x);
  top: var(--y);
}
</style>
