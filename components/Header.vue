<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const isScrolled = ref(false)

const handleScroll = () => {
  isScrolled.value = window.scrollY > 40
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll)
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})
</script>

<template>
  <header class="fixed top-0 left-0 w-full z-50 px-6 md:px-16 py-6">

    <div
      :class="[
        'max-w-7xl mx-auto flex justify-between items-center rounded-2xl px-8 transition-all duration-300 ease-out',
        isScrolled
          ? 'bg-white/[0.06] backdrop-blur-lg border border-white/10 shadow-[0_8px_32px_rgba(0,0,0,0.4)] py-4'
          : 'bg-transparent border border-transparent py-5'
      ]"
    >
      <!-- Logo -->
      <div class="flex justify-between items-center text-lg md:text-xl font-bold tracking-wider text-white">
        <img class="w-10" src="/public/images/logo-kelas.png" alt="">
        <div class="text pl-3">
         SOS<span class="text-red-500">25</span>
          </div>
    </div>

      <!-- Menu -->
      <nav>
        <ul class="flex gap-6 md:gap-10 text-sm uppercase tracking-wider text-gray-300">
          <li>
            <NuxtLink to="/" class="hover:text-white transition">
              Beranda
            </NuxtLink>
          </li>
          <li>
            <NuxtLink to="/galeri" class="hover:text-white transition">
              Galeri
            </NuxtLink>
          </li>
          <li>
            <NuxtLink to="/komentar" class="hover:text-white transition">
              Komentar
            </NuxtLink>
          </li>
        </ul>
      </nav>
    </div>

  </header>
</template>
