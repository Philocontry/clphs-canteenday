<script setup>
import { ref, onMounted } from 'vue'
import Footer from '@/components/footer.vue'
const { mainInfo } = defineProps({
  mainInfo: Object
})

const slide = ref(null)

const images = mainInfo.filter((r) => r.category == 'IMAGES' && r.status == 'OK')
const portrait = images
  .filter((r) => r.orientation.toLowerCase().startsWith('p'))
  .sort(() => {
    return 0.5 - Math.random()
  })
  .slice(0, 15)
const landscape = images
  .filter((r) => r.orientation.toLowerCase().startsWith('l'))
  .sort(() => {
    return 0.5 - Math.random()
  })
  .slice(0, 18)

onMounted(() => {
  const observer = new IntersectionObserver((entries) => {
    entries.forEach((entry) => {
      if (entry.isIntersecting) {
        entry.target.classList.add('show')
      } else {
        entry.target.classList.remove('show')
      }
    })
  })
  slide.value.querySelectorAll('.hide').forEach((element) => {
    observer.observe(element)
  })
})

const currentPage = ref('食堂日')
const currentShowing = ref(images.filter((image) => image.location === currentPage.value))
const changeCurrentPage = (category) => {
  currentPage.value = category
  currentShowing.value = images.filter((image) => image.location === currentPage.value)
}
</script>
<template>
  <div class="absolute top-[100vh] w-full bg-[#d7d6d6]" id="about">
    <div
      class="grid grid-cols-2 gap-4 md:grid-cols-4 sm:p-16 p-8"
      ref="slide"
      v-if="portrait.length > 3 && landscape.length > 5"
    >
      <div class="grid gap-4">
        <div>
          <img
            class="h-auto max-w-full rounded-lg object-cover object-center hide"
            :src="portrait[0].url"
            alt="Campaign Images"
          />
        </div>
        <div>
          <img
            class="h-auto max-w-full rounded-lg object-cover object-center hide"
            :src="landscape[0].url"
            alt="Campaign Images"
          />
        </div>
        <div>
          <img
            class="h-auto max-w-full rounded-lg object-cover object-center hide"
            :src="landscape[1].url"
            alt="Campaign Images"
          />
        </div>
      </div>
      <div class="grid gap-4">
        <div>
          <img
            class="h-auto max-w-full rounded-lg object-cover object-center hide"
            :src="landscape[2].url"
            alt="Campaign Images"
          />
        </div>
        <div>
          <img
            class="h-auto max-w-full rounded-lg object-cover object-center hide"
            :src="portrait[1].url"
            alt="Campaign Images"
          />
        </div>
        <div>
          <img
            class="h-auto max-w-full rounded-lg object-cover object-center hide"
            :src="landscape[3].url"
            alt="Campaign Images"
          />
        </div>
      </div>
      <div class="grid gap-4">
        <div>
          <img
            class="h-auto max-w-full rounded-lg object-cover object-center hide"
            :src="portrait[2].url"
            alt="Campaign Images"
          />
        </div>
        <div>
          <img
            class="h-auto max-w-full rounded-lg object-cover object-center hide"
            :src="landscape[4].url"
            alt="Campaign Images"
          />
        </div>
        <div>
          <img
            class="h-auto max-w-full rounded-lg object-cover object-center hide"
            :src="landscape[5].url"
            alt="Campaign Images"
          />
        </div>
      </div>
      <div class="grid gap-4">
        <div>
          <img
            class="h-auto max-w-full rounded-lg object-cover object-center hide"
            :src="landscape[6].url"
            alt="Campaign Images"
          />
        </div>
        <div>
          <img
            class="h-auto max-w-full rounded-lg object-cover object-center hide"
            :src="landscape[7].url"
            alt="Campaign Images"
          />
        </div>
        <div>
          <img
            class="h-auto max-w-full rounded-lg object-cover object-center hide"
            :src="portrait[3].url"
            alt="Campaign Images"
          />
        </div>
      </div>
      <div class="grid gap-4">
        <div>
          <img
            class="h-auto max-w-full rounded-lg object-cover object-center hide"
            :src="landscape[8].url"
            alt="Campaign Images"
          />
        </div>
        <div>
          <img
            class="h-auto max-w-full rounded-lg object-cover object-center hide"
            :src="portrait[4].url"
            alt="Campaign Images"
          />
        </div>
        <div>
          <img
            class="h-auto max-w-full rounded-lg object-cover object-center hide"
            :src="landscape[9].url"
            alt="Campaign Images"
          />
        </div>
      </div>
      <div class="grid gap-4">
        <div>
          <img
            class="h-auto max-w-full rounded-lg object-cover object-center hide"
            :src="portrait[5].url"
            alt="Campaign Images"
          />
        </div>
        <div>
          <img
            class="h-auto max-w-full rounded-lg object-cover object-center hide"
            :src="landscape[10].url"
            alt="Campaign Images"
          />
        </div>
        <div>
          <img
            class="h-auto max-w-full rounded-lg object-cover object-center hide"
            :src="landscape[11].url"
            alt="Campaign Images"
          />
        </div>
      </div>
      <div class="grid gap-4">
        <div>
          <img
            class="h-auto max-w-full rounded-lg object-cover object-center hide"
            :src="landscape[12].url"
            alt="Campaign Images"
          />
        </div>
        <div>
          <img
            class="h-auto max-w-full rounded-lg object-cover object-center hide"
            :src="landscape[13].url"
            alt="Campaign Images"
          />
        </div>
        <div>
          <img
            class="h-auto max-w-full rounded-lg object-cover object-center hide"
            :src="portrait[6].url"
            alt="Campaign Images"
          />
        </div>
      </div>
      <div class="grid gap-4">
        <div>
          <img
            class="h-auto max-w-full rounded-lg object-cover object-center hide"
            :src="landscape[14].url"
            alt="Campaign Images"
          />
        </div>
        <div>
          <img
            class="h-auto max-w-full rounded-lg object-cover object-center hide"
            :src="portrait[7].url"
            alt="Campaign Images"
          />
        </div>
        <div>
          <img
            class="h-auto max-w-full rounded-lg object-cover object-center hide"
            :src="landscape[15].url"
            alt="Campaign Images"
          />
        </div>
      </div>
    </div>

    <h1 class="my-4 text-5xl tracking-tight font-extrabold text-gray-900 text-center">相片集</h1>
    <h1 class="my-4 text-2xl tracking-tight font-extrabold text-gray-900 text-center">Albums</h1>
    <div class="flex items-center justify-center py-4 md:py-8 flex-wrap sm:p-8 p-4">
      <button
        type="button"
        class="bg-white focus:ring-4 focus:outline-none rounded-full text-base font-medium px-5 py-2.5 text-center me-3 mb-3"
        @click="changeCurrentPage('食堂日')"
        :class="
          currentPage == '食堂日'
            ? 'text-blue-700 focus:ring-blue-300 border dark:border-blue-500 dark:text-blue-500 border-blue-600  dark:hover:text-white dark:hover:bg-blue-500 dark:bg-gray-900 dark:focus:ring-blue-800'
            : 'hover:scale-[1.1] ease-in-out transition hover:bg-blue-700 hover:text-white dark:text-white focus:ring-gray-300  dark:focus:ring-gray-800 text-gray-900 border border-white hover:border-gray-200 dark:border-gray-900 dark:bg-gray-900 dark:hover:border-gray-700'
        "
      >
        #食堂日
      </button>
      <button
        type="button"
        class="bg-white focus:ring-4 focus:outline-none rounded-full text-base font-medium px-5 py-2.5 text-center me-3 mb-3"
        @click="changeCurrentPage('试吃会')"
        :class="
          currentPage == '试吃会'
            ? 'text-blue-700 focus:ring-blue-300 border dark:border-blue-500 dark:text-blue-500 border-blue-600  dark:hover:text-white dark:hover:bg-blue-500 dark:bg-gray-900 dark:focus:ring-blue-800'
            : 'hover:scale-[1.1] ease-in-out transition hover:bg-blue-700 hover:text-white dark:text-white focus:ring-gray-300  dark:focus:ring-gray-800 text-gray-900 border border-white hover:border-gray-200 dark:border-gray-900 dark:bg-gray-900 dark:hover:border-gray-700'
        "
      >
        #试吃会
      </button>
      <button
        type="button"
        class="bg-white focus:ring-4 focus:outline-none rounded-full text-base font-medium px-5 py-2.5 text-center me-3 mb-3"
        @click="changeCurrentPage('乐队')"
        :class="
          currentPage == '乐队'
            ? 'text-blue-700 focus:ring-blue-300 border dark:border-blue-500 dark:text-blue-500 border-blue-600  dark:hover:text-white dark:hover:bg-blue-500 dark:bg-gray-900 dark:focus:ring-blue-800'
            : 'hover:scale-[1.1] ease-in-out transition hover:bg-blue-700 hover:text-white dark:text-white focus:ring-gray-300  dark:focus:ring-gray-800 text-gray-900 border border-white hover:border-gray-200 dark:border-gray-900 dark:bg-gray-900 dark:hover:border-gray-700'
        "
      >
        #乐队
      </button>
      <button
        type="button"
        class="bg-white focus:ring-4 focus:outline-none rounded-full text-base font-medium px-5 py-2.5 text-center me-3 mb-3"
        @click="changeCurrentPage('预热活动')"
        :class="
          currentPage == '预热活动'
            ? 'text-blue-700 focus:ring-blue-300 border dark:border-blue-500 dark:text-blue-500 border-blue-600  dark:hover:text-white dark:hover:bg-blue-500 dark:bg-gray-900 dark:focus:ring-blue-800'
            : 'hover:scale-[1.1] ease-in-out transition hover:bg-blue-700 hover:text-white dark:text-white focus:ring-gray-300  dark:focus:ring-gray-800 text-gray-900 border border-white hover:border-gray-200 dark:border-gray-900 dark:bg-gray-900 dark:hover:border-gray-700'
        "
      >
        #预热活动
      </button>
      <button
        type="button"
        class="bg-white focus:ring-4 focus:outline-none rounded-full text-base font-medium px-5 py-2.5 text-center me-3 mb-3"
        @click="changeCurrentPage('筹备')"
        :class="
          currentPage == '筹备'
            ? 'text-blue-700 focus:ring-blue-300 border dark:border-blue-500 dark:text-blue-500 border-blue-600  dark:hover:text-white dark:hover:bg-blue-500 dark:bg-gray-900 dark:focus:ring-blue-800'
            : 'hover:scale-[1.1] ease-in-out transition hover:bg-blue-700 hover:text-white dark:text-white focus:ring-gray-300  dark:focus:ring-gray-800 text-gray-900 border border-white hover:border-gray-200 dark:border-gray-900 dark:bg-gray-900 dark:hover:border-gray-700'
        "
      >
        #筹备
      </button>
    </div>
    <div class="grid grid-cols-2 md:grid-cols-3 gap-4 sm:p-16 p-8">
      <div class="w-full h-full" v-for="image in currentShowing">
        <a :href="image.url" :key="image.url" target="_blank">
          <img
            class="object-contain h-56 w-full rounded-lg bg-white/40"
            :src="image.url"
            loading="lazy"
            alt=""
          />
        </a>
      </div>
    </div>

    <Footer />
  </div>
</template>
