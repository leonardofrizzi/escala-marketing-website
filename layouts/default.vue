<template>
  <div class="relative min-h-screen">
    <AnimatedBackground />
    <div class="relative z-10">
      <Navbar />
      <slot />
      <Footer />
    </div>
    <CookieBanner />
    <WhatsAppFloat />
  </div>
</template>
