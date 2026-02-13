<script setup lang="ts">
import { Menu, X } from 'lucide-vue-next'

const mobileOpen = ref(false)
const scrolled = ref(false)

const links = [
  { label: 'Home', href: '/' },
  { label: 'Serviços', href: '/#servicos' },
  { label: 'Sobre', href: '/#sobre' },
  { label: 'Contato', href: '/#contato' },
]

const toggleMobile = () => {
  mobileOpen.value = !mobileOpen.value
}

const closeMobile = () => {
  mobileOpen.value = false
}

const onScroll = () => {
  scrolled.value = window.scrollY > 20
}

onMounted(() => {
  window.addEventListener('scroll', onScroll, { passive: true })
})

onUnmounted(() => {
  window.removeEventListener('scroll', onScroll)
})
</script>

<template>
  <nav
    class="fixed left-0 right-0 top-0 z-50 transition-all duration-300"
    :class="scrolled ? 'bg-dark/70 backdrop-blur-xl border-b border-white/5' : 'bg-transparent'"
  >
    <div class="mx-auto flex h-20 max-w-7xl items-center justify-between px-6 lg:px-10">
      <!-- Logo -->
      <NuxtLink to="/" class="relative z-10" @click="closeMobile">
        <img
          src="/escalamarketing.webp"
          alt="Escala Digital"
          class="h-12 w-auto"
        >
      </NuxtLink>

      <!-- Links desktop -->
      <div class="hidden items-center gap-10 md:flex">
        <NuxtLink
          v-for="link in links"
          :key="link.href"
          :to="link.href"
          class="text-sm font-light tracking-wide text-white/60 transition-colors duration-200 hover:text-white"
        >
          {{ link.label }}
        </NuxtLink>

        <NuxtLink
          to="/#contato"
          class="inline-flex items-center gap-2 rounded-full border border-white/15 bg-white/5 px-6 py-2.5 text-sm font-light tracking-wide text-white transition-all duration-200 hover:border-white/30 hover:bg-white/10"
        >
          <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="currentColor"><path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 01-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 01-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 012.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0012.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 005.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 00-3.48-8.413z"/></svg>
          Fale Conosco
        </NuxtLink>
      </div>

      <!-- Hamburger mobile -->
      <button
        class="relative z-10 text-white md:hidden"
        aria-label="Menu"
        @click="toggleMobile"
      >
        <X v-if="mobileOpen" :size="24" :stroke-width="1.5" />
        <Menu v-else :size="24" :stroke-width="1.5" />
      </button>
    </div>

    <!-- Menu mobile -->
    <Transition
      enter-active-class="transition-all duration-300 ease-out"
      leave-active-class="transition-all duration-200 ease-in"
      enter-from-class="opacity-0"
      enter-to-class="opacity-100"
      leave-from-class="opacity-100"
      leave-to-class="opacity-0"
    >
      <div
        v-if="mobileOpen"
        class="absolute inset-x-0 top-0 min-h-screen bg-dark/95 backdrop-blur-2xl md:hidden"
      >
        <div class="flex flex-col items-center justify-center gap-8 pt-32">
          <NuxtLink
            v-for="link in links"
            :key="link.href"
            :to="link.href"
            class="text-2xl font-light tracking-wide text-white/70 transition-colors hover:text-white"
            @click="closeMobile"
          >
            {{ link.label }}
          </NuxtLink>

          <NuxtLink
            to="/#contato"
            class="mt-4 inline-flex items-center gap-2.5 rounded-full border border-white/15 bg-white/5 px-8 py-3 text-lg font-light tracking-wide text-white transition-all hover:border-white/30 hover:bg-white/10"
            @click="closeMobile"
          >
            <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="currentColor"><path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 01-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 01-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 012.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0012.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 005.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 00-3.48-8.413z"/></svg>
            Fale Conosco
          </NuxtLink>
        </div>
      </div>
    </Transition>
  </nav>
</template>
