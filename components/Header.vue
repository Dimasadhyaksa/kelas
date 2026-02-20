<script setup>
import { ref, onMounted, onUnmounted } from "vue"

const showHeader = ref(true)
let lastScroll = 0

const handleScroll = () => {
  const currentScroll = window.scrollY

  if (currentScroll <= 10) {
    showHeader.value = true
  } else if (currentScroll > lastScroll) {
    showHeader.value = false
  } else {
    showHeader.value = true
  }

  lastScroll = currentScroll
}

onMounted(() => {
  window.addEventListener("scroll", handleScroll)
})

onUnmounted(() => {
  window.removeEventListener("scroll", handleScroll)
})
</script>


<template>
  <header
    :class="[
      'fixed top-0 left-0 w-full z-50 px-6 md:px-16 py-6 transition-all duration-500 ease-in-out',
      showHeader 
        ? 'opacity-100 blur-0 pointer-events-auto'
        : 'opacity-0 blur-sm pointer-events-none'
    ]"
  >
    <div
      class="max-w-7xl mx-auto flex justify-between items-center 
             rounded-2xl px-8 py-4
             bg-white/[0.04] backdrop-blur-md 
             border border-white/10
             shadow-[0_8px_32px_rgba(0,0,0,0.4)]"
    >
      <!-- Logo -->
      <div class="flex items-center text-lg md:text-xl font-bold tracking-wider text-white">
        <img class="w-10" src="/images/logo-kelas.png" alt="">
        <div class="pl-3">
          SOS<span class="text-red-500">25</span>
        </div>
      </div>

      <!-- Menu -->
      <nav>
        <ul class="flex gap-6 md:gap-10 text-sm uppercase tracking-wider text-gray-300">
          <li><NuxtLink to="/" class="hover:text-white transition">Beranda</NuxtLink></li>
          <li><NuxtLink to="/galeri" class="hover:text-white transition">Galeri</NuxtLink></li>
          <li><NuxtLink to="/" class="hover:text-white transition">Komentar</NuxtLink></li>
        </ul>
      </nav>
    </div>
  </header>
</template>
