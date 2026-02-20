<script setup>
import { ref, computed } from "vue"

const rating = ref(3)

/* ICON STATE */
const ratingState = computed(() => {
  if (rating.value >= 4) return "happy"
  if (rating.value >= 2.5) return "neutral"
  return "sad"
})
</script>

<template>
  <footer class="relative w-full bg-[#0b0f18] text-white pt-28 pb-12 overflow-hidden">

    <!-- Background Glow -->
    <div class="absolute -top-40 left-1/2 -translate-x-1/2 w-[600px] h-[600px] 
                bg-red-600/10 blur-[160px] rounded-full pointer-events-none">
    </div>

    <div class="relative max-w-7xl mx-auto px-6 md:px-20">

      <!-- GRID -->
      <div class="grid md:grid-cols-4 gap-16">

        <!-- LOGO -->
        <div>
          <img 
            src="/images/logo-kelas.png" 
            class="w-20 opacity-80 hover:opacity-100 transition duration-300"
          />
          <p class="mt-6 text-sm text-gray-500 leading-relaxed">
            Creative student movement building digital presence and innovation.
          </p>
        </div>

        <!-- CREATED BY -->
        <div>
          <h3 class="uppercase text-xs tracking-widest mb-6 text-gray-500">
            Created By
          </h3>
          <ul class="space-y-4 text-gray-300">
            <li class="hover:text-white transition cursor-pointer relative group">
              <a href="https://www.instagram.com/dimasadhyaksa_?igsh=MTFkcDgxeXNjZjQweQ==" target="blank">DYMZ</a>
              <span class="absolute left-0 -bottom-1 w-0 h-[1px] bg-red-500 
                           transition-all duration-300 group-hover:w-full">
              </span>
            </li>
          </ul>
        </div>

        <!-- FOLLOW -->
        <div>
          <h3 class="uppercase text-xs tracking-widest mb-6 text-gray-500">
            Follow Us
          </h3>
          <ul class="space-y-4 text-gray-300">
            <li class="hover:text-red-500 transition cursor-pointer relative group">
              <a href="https://www.instagram.com/class_a1_informatics?igsh=eW4yb2FmYWVuY3Zp" target="blank">Instagram</a>
              <span class="absolute left-0 -bottom-1 w-0 h-[1px] bg-red-500 
                           transition-all duration-300 group-hover:w-full">
              </span>
            </li>
            <li class="hover:text-red-500 transition cursor-pointer relative group">
              Youtube
              <span class="absolute left-0 -bottom-1 w-0 h-[1px] bg-red-500 
                           transition-all duration-300 group-hover:w-full">
              </span>
            </li>
          </ul>
        </div>

        <!-- RATE -->
<div>
  <h3 class="uppercase text-xs tracking-widest mb-6 text-gray-500">
    Rate Us
  </h3>

  <div class="flex items-center justify-between mb-4">

    <!-- ICON -->
    <div class="w-8 h-8 text-red-500 transition-all duration-300">

      <!-- HAPPY -->
      <svg
        v-if="ratingState === 'happy'"
        viewBox="0 0 24 24"
        fill="none"
        stroke="currentColor"
        stroke-width="2"
        class="w-full h-full opacity-80"
      >
        <circle xmlns="http://www.w3.org/2000/svg" cx="12" cy="12" r="10" stroke="#33363F" stroke-width="2" stroke-linecap="round"/>
        <path xmlns="http://www.w3.org/2000/svg" d="M7.88124 15.7559C8.37391 16.1826 9.02309 16.4909 9.72265 16.6928C10.4301 16.897 11.2142 17 12 17C12.7858 17 13.5699 16.897 14.2774 16.6928C14.9769 16.4909 15.6261 16.1826 16.1188 15.7559" stroke="#33363F" stroke-width="2" stroke-linecap="round"/>
        <circle xmlns="http://www.w3.org/2000/svg" cx="9" cy="10" r="1.25" fill="#33363F" stroke="#33363F" stroke-width="0.5" stroke-linecap="round"/>
        <circle xmlns="http://www.w3.org/2000/svg" cx="15" cy="10" r="1.25" fill="#33363F" stroke="#33363F" stroke-width="0.5" stroke-linecap="round"/>
      </svg>

      <!-- NEUTRAL -->
      <svg
        v-else-if="ratingState === 'neutral'"
        viewBox="0 0 24 24"
        fill="none"
        stroke="currentColor"
        stroke-width="2"
        class="w-full h-full opacity-70"
      >
        <circle xmlns="http://www.w3.org/2000/svg" cx="12" cy="12" r="10" stroke="#33363F" stroke-width="2" stroke-linecap="round"/>
        <circle xmlns="http://www.w3.org/2000/svg" cx="9" cy="9" r="1.25" fill="#33363F" stroke="#33363F" stroke-width="0.5" stroke-linecap="round"/>
        <circle xmlns="http://www.w3.org/2000/svg" cx="15" cy="9" r="1.25" fill="#33363F" stroke="#33363F" stroke-width="0.5" stroke-linecap="round"/>
        <path xmlns="http://www.w3.org/2000/svg" d="M15 15.5C15 16.8807 13.6569 18 12 18C10.3431 18 9 16.8807 9 15.5C9 14.1193 10.3431 13 12 13C13.6569 13 15 14.1193 15 15.5Z" fill="#33363F"/>
      </svg>

      <!-- SAD -->
      <svg
        v-else
        viewBox="0 0 24 24"
        fill="none"
        stroke="currentColor"
        stroke-width="2"
        class="w-full h-full opacity-70"
      >
        <circle cx="12" cy="12" r="9"/>
        <path d="M8 16s1.5-2 4-2 4 2 4 2"/>
        <line x1="9" y1="10" x2="9.01" y2="10"/>
        <line x1="15" y1="10" x2="15.01" y2="10"/>
      </svg>

    </div>

    <!-- VALUE -->
    <span class="text-base font-semibold text-gray-300">
      {{ rating.toFixed(1) }}
    </span>
  </div>

  <!-- SLIDER -->
  <input
    type="range"
    min="0"
    max="5"
    step="0.5"
    v-model.number="rating"
    class="w-full slider"
  />
</div>

      </div>

      <!-- Gradient Divider -->
      <div class="mt-16 h-[1px] w-full bg-gradient-to-r 
                  from-transparent via-white/10 to-transparent">
      </div>

      <!-- COPYRIGHT -->
      <div class="pt-6 text-gray-500 text-sm">
        © 2026 SOS 25 | Di Kelola Oleh Mahasiswa
      </div>

    </div>

  </footer>
</template>
