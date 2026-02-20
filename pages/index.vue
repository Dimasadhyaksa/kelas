<script setup>
import AboutUs from '~/components/AboutUs.vue'
import TeamCarousel from '~/components/TeamCarousel.vue'
import ImageCarousel from '~/components/ImageCarousel.vue'
import Coment from '~/components/Coment.vue'

const images = [
  '/images/foto1.jpg',
  '/images/foto2.jpg',
  '/images/foto3.jpg'
]

const bgImages = Array(40).fill(images).flat()
</script>

<template>
<section class="relative w-full min-h-screen overflow-hidden text-white">

  <!-- ================= BACKGROUND ================= -->
  <div class="absolute inset-0 overflow-hidden">

    <div class="mosaic animate-slide">
      <div
        v-for="(img, i) in bgImages"
        :key="i"
        class="mosaic-item"
        :style="{ backgroundImage: `url(${img})` }"
      />
    </div>

    <div class="absolute inset-0 bg-black/75"></div>
  </div>

  <!-- GRADIENT -->
  <div class="absolute inset-0 bg-gradient-to-r from-black via-red-900/40 to-black"></div>

  <!-- ================= CONTENT ================= -->
  <div
    class="relative z-10 max-w-7xl mx-auto
           px-6 md:px-20 py-32
           flex flex-col md:flex-row
           items-center justify-between gap-12"
  >

    <!-- ========= TEXT ========= -->
    <div class="max-w-xl text-center md:text-left">

      <p class="uppercase tracking-widest text-gray-300 text-sm">
        SELAMAT DATANG DI
      </p>

      <h1 class="text-4xl md:text-6xl lg:text-7xl font-extrabold mt-4">
        SHADLE OUR STRUGGLE
        <span class="text-red-500">25</span>
      </h1>

      <p class="mt-6 text-gray-300">
        Website dokumentasi dan informasi kegiatan kami.
      </p>

      <NuxtLink
        to="/galeri"
        class="inline-block mt-8
               bg-red-600 hover:bg-red-500
               transition duration-300
               px-8 py-3 rounded-full
               hover:scale-105 shadow-lg shadow-red-600/30"
      >
        Selengkapnya →
      </NuxtLink>

    </div>

    <!-- ========= 3D FOTO (DESKTOP ONLY) ========= -->
    <!-- hidden di mobile, muncul mulai md -->
    <div
      class="hidden md:block
             transform rotate-6
             hover:rotate-0 hover:scale-105
             transition duration-500"
    >
      <div class="bg-white p-4 rounded-xl shadow-2xl">
        <img
          src="/public/images/foto2.jpg"
          class="w-72 object-cover rounded-md"
        />
      </div>
    </div>

  </div>
</section>

<AboutUs/>
<TeamCarousel/>
<ImageCarousel/>
<Coment/>

</template>

<style scoped>

/* MOSAIC GRID */
.mosaic {
  display: grid;
  grid-template-columns: repeat(8, 1fr);
  gap: 20px;
  width: 200%;
  transform: rotate(-10deg) scale(1.3);
}

@media (max-width: 768px) {
  .mosaic {
    grid-template-columns: repeat(4, 1fr);
  }
}

.mosaic-item {
  height: 180px;
  background-size: cover;
  background-position: center;
  border-radius: 20px;
  opacity: 0.28;
}

/* ANIMATION */
@keyframes slide {
  0% {
    transform: translateX(0) rotate(-10deg) scale(1.3);
  }
  100% {
    transform: translateX(-50%) rotate(-10deg) scale(1.3);
  }
}

.animate-slide {
  animation: slide 40s linear infinite;
}

</style>
