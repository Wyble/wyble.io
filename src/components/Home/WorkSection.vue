<script setup lang="ts">
import { computed, ref } from 'vue'

const selected = ref('all')
const categories = [
  { name: 'View All', key: 'all', count: 0 },
  { name: 'Web Design', key: 'web', count: 5 },
  { name: 'Mobile Apps', key: 'mobile', count: 6 },
  { name: 'Desktop Apps', key: 'desktop', count: 4 },
  { name: 'Case Studies', key: 'case_study', count: 7 },
  { name: 'Films', key: 'film', count: 3 }
]

const total = categories.reduce((prev, curr) => (prev += curr.count), 0)
categories[0].count = total

const projects = [
  {
    name: 'Elegant Homes',
    category: 'web',
    description: 'A modern and visually stunning website for a real estate agency.'
  },
  {
    name: 'FoodieFusion',
    category: 'web',
    description:
      'A dynamic and interactive website for a food blog, featuring recipes and culinary tips.'
  },
  {
    name: 'SwiftCab',
    category: 'web',
    description:
      'A user-friendly website and booking platform for a transportation service company.'
  },
  {
    name: 'ArtGalleryX',
    category: 'web',
    description:
      'An elegant and immersive website showcasing a collection of contemporary artworks.'
  },
  {
    name: 'SportsHub',
    category: 'web',
    description: 'A sports news website with real-time updates, scores, and player profiles.'
  },
  {
    name: 'FitnessTrack',
    category: 'mobile',
    description:
      'A fitness tracking app that helps users monitor their exercise routines and progress.'
  },
  {
    name: 'TravelPilot',
    category: 'mobile',
    description:
      'A comprehensive travel app with destination guides, booking features, and itinerary planning.'
  },
  {
    name: 'HealthQuest',
    category: 'mobile',
    description:
      'A health and wellness app that provides personalized fitness plans and nutritional guidance.'
  },
  {
    name: 'SocialConnect',
    category: 'mobile',
    description:
      'A social networking app that allows users to connect, share updates, and discover new communities.'
  },
  {
    name: 'FinanceMaster',
    category: 'mobile',
    description:
      'A financial management app for budgeting, expense tracking, and investment analysis.'
  },
  {
    name: 'ProductivityPlus',
    category: 'mobile',
    description:
      'A productivity app that helps users organize tasks, manage schedules, and track goals.'
  },
  {
    name: 'ProjectXpert',
    category: 'desktop',
    description: 'A project management software for efficient team collaboration and task tracking.'
  },
  {
    name: 'DataAnalyzer',
    category: 'desktop',
    description:
      'A powerful data analysis tool with advanced visualization and statistical capabilities.'
  },
  {
    name: 'InventoryPro',
    category: 'desktop',
    description: 'An inventory management system for tracking stock, sales, and order fulfillment.'
  },
  {
    name: 'TimeKeeper',
    category: 'desktop',
    description:
      'A time tracking software for professionals to manage and analyze their work hours.'
  },
  {
    name: 'CaseStudyA',
    category: 'case_study',
    description:
      'An in-depth analysis of a successful digital marketing campaign for a global brand.'
  },
  {
    name: 'CaseStudyB',
    category: 'case_study',
    description: 'A comprehensive study on user experience optimization for an e-commerce platform.'
  },
  {
    name: 'CaseStudyC',
    category: 'case_study',
    description:
      'Exploring the impact of data-driven decision making on business growth and profitability.'
  },
  {
    name: 'CaseStudyD',
    category: 'case_study',
    description:
      'A strategic rebranding case study showcasing the transformation of a well-established company.'
  },
  {
    name: 'CaseStudyE',
    category: 'case_study',
    description:
      'Analyzing the user acquisition and retention strategies employed by a popular mobile app.'
  },
  {
    name: 'FilmProject1',
    category: 'film',
    description: 'A gripping short film exploring the human psyche in the face of adversity.'
  },
  {
    name: 'FilmProject2',
    category: 'film',
    description:
      'A visually stunning documentary capturing the beauty and diversity of underwater life.'
  },
  {
    name: 'FilmProject3',
    category: 'film',
    description: 'An inspiring feature film based on the true story of an extraordinary individual.'
  },
  {
    name: 'FilmProject4',
    category: 'film',
    description:
      'A thought-provoking animated film that delves into the complexities of societal issues.'
  },
  {
    name: 'FilmProject5',
    category: 'film',
    description: 'A heartwarming short film portraying the power of human connections and kindness.'
  }
]

const filterProjects = computed(() =>
  projects.filter((project) => selected.value === 'all' || project.category === selected.value)
)
</script>

<template>
  <section class="min-h-screen">
    <div class="md:mt-52 pt-32 pb-16 mx-4 xl:mx-auto">
      <h2 class="text-4xl mb-4">Inspiring Highlights of Our Digital Creations</h2>

      <div class="flex flex-wrap justify-center xl:justify-start">
        <button
          v-auto-animate
          v-for="category in categories"
          :key="category.key"
          @click="selected = category.key"
          :class="selected === category.key ? 'border-violet-400 bg-violet-600 bg-opacity-50 ' : ''"
          class="m-1 py-3 px-5 rounded-full border text-neutral-300 font-bold inline-flex items-center justify-center gap-2 transition-colors duration-300"
        >
          {{ category.name }}
          <svg
            v-if="category.key === 'web'"
            xmlns="http://www.w3.org/2000/svg"
            fill="none"
            viewBox="0 0 24 24"
            stroke-width="1.5"
            stroke="currentColor"
            class="w-6 h-6"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              d="M12 21a9.004 9.004 0 008.716-6.747M12 21a9.004 9.004 0 01-8.716-6.747M12 21c2.485 0 4.5-4.03 4.5-9S14.485 3 12 3m0 18c-2.485 0-4.5-4.03-4.5-9S9.515 3 12 3m0 0a8.997 8.997 0 017.843 4.582M12 3a8.997 8.997 0 00-7.843 4.582m15.686 0A11.953 11.953 0 0112 10.5c-2.998 0-5.74-1.1-7.843-2.918m15.686 0A8.959 8.959 0 0121 12c0 .778-.099 1.533-.284 2.253m0 0A17.919 17.919 0 0112 16.5c-3.162 0-6.133-.815-8.716-2.247m0 0A9.015 9.015 0 013 12c0-1.605.42-3.113 1.157-4.418"
            />
          </svg>
          <svg
            v-else-if="category.key === 'mobile'"
            xmlns="http://www.w3.org/2000/svg"
            fill="none"
            viewBox="0 0 24 24"
            stroke-width="1.5"
            stroke="currentColor"
            class="w-6 h-6"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              d="M10.5 1.5H8.25A2.25 2.25 0 006 3.75v16.5a2.25 2.25 0 002.25 2.25h7.5A2.25 2.25 0 0018 20.25V3.75a2.25 2.25 0 00-2.25-2.25H13.5m-3 0V3h3V1.5m-3 0h3m-3 18.75h3"
            />
          </svg>
          <svg
            v-else-if="category.key === 'desktop'"
            xmlns="http://www.w3.org/2000/svg"
            fill="none"
            viewBox="0 0 24 24"
            stroke-width="1.5"
            stroke="currentColor"
            class="w-6 h-6"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              d="M9 17.25v1.007a3 3 0 01-.879 2.122L7.5 21h9l-.621-.621A3 3 0 0115 18.257V17.25m6-12V15a2.25 2.25 0 01-2.25 2.25H5.25A2.25 2.25 0 013 15V5.25m18 0A2.25 2.25 0 0018.75 3H5.25A2.25 2.25 0 003 5.25m18 0V12a2.25 2.25 0 01-2.25 2.25H5.25A2.25 2.25 0 013 12V5.25"
            />
          </svg>
          <svg
            v-else-if="category.key === 'case_study'"
            xmlns="http://www.w3.org/2000/svg"
            fill="none"
            viewBox="0 0 24 24"
            stroke-width="1.5"
            stroke="currentColor"
            class="w-6 h-6"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              d="M9.53 16.122a3 3 0 00-5.78 1.128 2.25 2.25 0 01-2.4 2.245 4.5 4.5 0 008.4-2.245c0-.399-.078-.78-.22-1.128zm0 0a15.998 15.998 0 003.388-1.62m-5.043-.025a15.994 15.994 0 011.622-3.395m3.42 3.42a15.995 15.995 0 004.764-4.648l3.876-5.814a1.151 1.151 0 00-1.597-1.597L14.146 6.32a15.996 15.996 0 00-4.649 4.763m3.42 3.42a6.776 6.776 0 00-3.42-3.42"
            />
          </svg>
          <svg
            v-else-if="category.key === 'film'"
            xmlns="http://www.w3.org/2000/svg"
            fill="none"
            viewBox="0 0 24 24"
            stroke-width="1.5"
            stroke="currentColor"
            class="w-6 h-6"
          >
            <path
              stroke-linecap="round"
              d="M15.75 10.5l4.72-4.72a.75.75 0 011.28.53v11.38a.75.75 0 01-1.28.53l-4.72-4.72M4.5 18.75h9a2.25 2.25 0 002.25-2.25v-9a2.25 2.25 0 00-2.25-2.25h-9A2.25 2.25 0 002.25 7.5v9a2.25 2.25 0 002.25 2.25z"
            />
          </svg>
          <span
            :class="
              selected === category.key
                ? 'bg-violet-800 bg-opacity-50'
                : 'bg-neutral-800 bg-opacity-80'
            "
            class="rounded-full px-3 transition-colors duration-700"
            >{{ category.count }}</span
          >
        </button>
      </div>

      <ul
        class="py-8 grid grid-cols-1 md:grid-cols-2 xl:grid-cols-4 place-items-center gap-4"
        v-auto-animate
      >
        <li v-for="project in filterProjects" :key="project.name" class="h-full">
          <article
            class="flex flex-col items-center max-w-xs border border-neutral-800 p-4 rounded-3xl h-full"
          >
            <div
              :class="
                project.category === 'web'
                  ? 'bg-blue-600'
                  : project.category === 'mobile'
                  ? 'bg-pink-600'
                  : project.category === 'desktop'
                  ? 'bg-green-600'
                  : project.category === 'case_study'
                  ? 'bg-orange-600'
                  : 'bg-violet-600'
              "
              class="rounded-full flex items-center justify-center w-16 aspect-square"
            >
              <svg
                v-if="project.category === 'web'"
                xmlns="http://www.w3.org/2000/svg"
                fill="none"
                viewBox="0 0 24 24"
                stroke-width="1.5"
                stroke="currentColor"
                class="w-6 h-6"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  d="M12 21a9.004 9.004 0 008.716-6.747M12 21a9.004 9.004 0 01-8.716-6.747M12 21c2.485 0 4.5-4.03 4.5-9S14.485 3 12 3m0 18c-2.485 0-4.5-4.03-4.5-9S9.515 3 12 3m0 0a8.997 8.997 0 017.843 4.582M12 3a8.997 8.997 0 00-7.843 4.582m15.686 0A11.953 11.953 0 0112 10.5c-2.998 0-5.74-1.1-7.843-2.918m15.686 0A8.959 8.959 0 0121 12c0 .778-.099 1.533-.284 2.253m0 0A17.919 17.919 0 0112 16.5c-3.162 0-6.133-.815-8.716-2.247m0 0A9.015 9.015 0 013 12c0-1.605.42-3.113 1.157-4.418"
                />
              </svg>
              <svg
                v-else-if="project.category === 'mobile'"
                xmlns="http://www.w3.org/2000/svg"
                fill="none"
                viewBox="0 0 24 24"
                stroke-width="1.5"
                stroke="currentColor"
                class="w-6 h-6"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  d="M10.5 1.5H8.25A2.25 2.25 0 006 3.75v16.5a2.25 2.25 0 002.25 2.25h7.5A2.25 2.25 0 0018 20.25V3.75a2.25 2.25 0 00-2.25-2.25H13.5m-3 0V3h3V1.5m-3 0h3m-3 18.75h3"
                />
              </svg>
              <svg
                v-else-if="project.category === 'desktop'"
                xmlns="http://www.w3.org/2000/svg"
                fill="none"
                viewBox="0 0 24 24"
                stroke-width="1.5"
                stroke="currentColor"
                class="w-6 h-6"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  d="M9 17.25v1.007a3 3 0 01-.879 2.122L7.5 21h9l-.621-.621A3 3 0 0115 18.257V17.25m6-12V15a2.25 2.25 0 01-2.25 2.25H5.25A2.25 2.25 0 013 15V5.25m18 0A2.25 2.25 0 0018.75 3H5.25A2.25 2.25 0 003 5.25m18 0V12a2.25 2.25 0 01-2.25 2.25H5.25A2.25 2.25 0 013 12V5.25"
                />
              </svg>
              <svg
                v-else-if="project.category === 'case_study'"
                xmlns="http://www.w3.org/2000/svg"
                fill="none"
                viewBox="0 0 24 24"
                stroke-width="1.5"
                stroke="currentColor"
                class="w-6 h-6"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  d="M9.53 16.122a3 3 0 00-5.78 1.128 2.25 2.25 0 01-2.4 2.245 4.5 4.5 0 008.4-2.245c0-.399-.078-.78-.22-1.128zm0 0a15.998 15.998 0 003.388-1.62m-5.043-.025a15.994 15.994 0 011.622-3.395m3.42 3.42a15.995 15.995 0 004.764-4.648l3.876-5.814a1.151 1.151 0 00-1.597-1.597L14.146 6.32a15.996 15.996 0 00-4.649 4.763m3.42 3.42a6.776 6.776 0 00-3.42-3.42"
                />
              </svg>
              <svg
                v-else
                xmlns="http://www.w3.org/2000/svg"
                fill="none"
                viewBox="0 0 24 24"
                stroke-width="1.5"
                stroke="currentColor"
                class="w-6 h-6"
              >
                <path
                  stroke-linecap="round"
                  d="M15.75 10.5l4.72-4.72a.75.75 0 011.28.53v11.38a.75.75 0 01-1.28.53l-4.72-4.72M4.5 18.75h9a2.25 2.25 0 002.25-2.25v-9a2.25 2.25 0 00-2.25-2.25h-9A2.25 2.25 0 002.25 7.5v9a2.25 2.25 0 002.25 2.25z"
                />
              </svg>
            </div>
            <h3 class="my-2 text-xl font-bold">{{ project.name }}</h3>
            <p class="mb-8 text-lg leading-normal tracking-tighter text-start">
              {{ project.description }}
            </p>
          </article>
        </li>
      </ul>
    </div>
  </section>
</template>
