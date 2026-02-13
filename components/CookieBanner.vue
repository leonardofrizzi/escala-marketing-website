<script setup lang="ts">
const visible = ref(false)

onMounted(() => {
  if (!localStorage.getItem('cookies-accepted')) {
    visible.value = true
  }
})

function accept() {
  localStorage.setItem('cookies-accepted', 'true')
  visible.value = false
}
</script>

<template>
  <Transition
    enter-active-class="transition-all duration-300 ease-out"
    enter-from-class="translate-y-full opacity-0"
    enter-to-class="translate-y-0 opacity-100"
    leave-active-class="transition-all duration-200 ease-in"
    leave-from-class="translate-y-0 opacity-100"
    leave-to-class="translate-y-full opacity-0"
  >
    <div
      v-if="visible"
      class="fixed bottom-0 left-0 right-0 z-50 border-t border-white/[0.08] bg-dark/90 backdrop-blur-xl"
    >
      <div class="mx-auto flex max-w-7xl flex-col items-center justify-between gap-4 px-6 py-4 md:flex-row lg:px-10">
        <p class="text-center text-sm font-light text-white/60 md:text-left">
          Utilizamos cookies para melhorar sua experiência. Ao continuar navegando, você concorda com nossa
          <NuxtLink to="/politica-de-privacidade" class="text-white/80 underline underline-offset-2 transition-colors hover:text-white">Política de Privacidade</NuxtLink>.
        </p>
        <button
          class="shrink-0 rounded-full bg-white px-6 py-2 text-sm font-medium tracking-wide text-dark transition-all duration-200 hover:bg-white/90"
          @click="accept"
        >
          Aceitar
        </button>
      </div>
    </div>
  </Transition>
</template>
