<template>
  <footer class="border-t border-white/[0.06] py-8">
    <div class="mx-auto flex max-w-7xl flex-col items-center justify-between gap-4 px-6 md:flex-row lg:px-10">
      <p class="text-xs font-light text-white/60">
        &copy; {{ new Date().getFullYear() }} Escala Digital. Todos os direitos reservados.
      </p>
      <NuxtLink to="/politica-de-privacidade" class="text-xs font-light text-white/60 transition-colors hover:text-white/60">
        Política de Privacidade
      </NuxtLink>
    </div>
  </footer>
</template>
