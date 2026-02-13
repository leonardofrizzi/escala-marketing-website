<script setup lang="ts">
import { gsap } from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'

const containerRef = ref<HTMLElement>()

// paletas por "zona" de scroll — cada zona muda o clima visual
const palettes = [
  // Hero — azul/roxo frio
  ['#4f6ef7', '#6366f1', '#a855f7', '#3b82f6', '#818cf8'],
  // Diferenciais/Serviços — roxo/magenta quente
  ['#a855f7', '#ec4899', '#d946ef', '#8b5cf6', '#f472b6'],
  // Sobre Nós — verde/ciano
  ['#10b981', '#06b6d4', '#14b8a6', '#22d3ee', '#34d399'],
  // Contato — laranja/rosa quente
  ['#f97316', '#ef4444', '#f59e0b', '#ec4899', '#fb923c'],
  // FAQ — azul royal/índigo
  ['#3b82f6', '#6366f1', '#2563eb', '#4f46e5', '#60a5fa'],
]

onMounted(() => {
  if (import.meta.server) return
  if (!containerRef.value) return

  gsap.registerPlugin(ScrollTrigger)

  const blobs = containerRef.value.querySelectorAll('.gradient-blob')

  // movimento base — mais amplo e rápido
  blobs.forEach((blob, i) => {
    // movimento XY amplo
    gsap.to(blob, {
      x: () => gsap.utils.random(-350, 350),
      y: () => gsap.utils.random(-300, 300),
      scale: () => gsap.utils.random(0.6, 1.6),
      duration: gsap.utils.random(3, 5),
      repeat: -1,
      yoyo: true,
      ease: 'sine.inOut',
      delay: i * 0.5,
    })

    // rotação
    gsap.to(blob, {
      rotation: gsap.utils.random(-45, 45),
      duration: gsap.utils.random(5, 9),
      repeat: -1,
      yoyo: true,
      ease: 'sine.inOut',
    })

    // pulso de opacidade
    gsap.to(blob, {
      opacity: () => gsap.utils.random(0.25, 0.6),
      duration: gsap.utils.random(2, 4),
      repeat: -1,
      yoyo: true,
      ease: 'sine.inOut',
      delay: i * 0.3,
    })
  })

  // transição de cores baseada no scroll
  const sections = document.querySelectorAll('section')

  sections.forEach((section, sIndex) => {
    const paletteIndex = Math.min(sIndex, palettes.length - 1)
    const colors = palettes[paletteIndex]

    ScrollTrigger.create({
      trigger: section,
      start: 'top 60%',
      end: 'bottom 40%',
      onEnter: () => morphColors(blobs, colors),
      onEnterBack: () => morphColors(blobs, colors),
    })
  })

  // cor inicial
  morphColors(blobs, palettes[0])
})

function morphColors(blobs: NodeListOf<Element>, colors: string[]) {
  blobs.forEach((blob, i) => {
    const color = colors[i % colors.length]
    gsap.to(blob, {
      '--blob-color': color,
      duration: 1.8,
      ease: 'power2.inOut',
      onUpdate() {
        const el = blob as HTMLElement
        const c = getComputedStyle(el).getPropertyValue('--blob-color').trim() || color
        el.style.background = `radial-gradient(circle, ${c}, transparent 65%)`
      },
    })
  })
}
</script>

<template>
  <div ref="containerRef" class="pointer-events-none fixed inset-0 z-0 overflow-hidden">
    <div
      class="gradient-blob absolute -left-20 -top-20 h-[600px] w-[600px] rounded-full opacity-40 blur-[100px]"
      style="--blob-color: #4f6ef7; background: radial-gradient(circle, #4f6ef7, transparent 65%)"
    />

    <div
      class="gradient-blob absolute -right-10 top-[10%] h-[700px] w-[700px] rounded-full opacity-40 blur-[100px]"
      style="--blob-color: #6366f1; background: radial-gradient(circle, #6366f1, transparent 65%)"
    />

    <div
      class="gradient-blob absolute bottom-[5%] left-[15%] h-[550px] w-[550px] rounded-full opacity-35 blur-[100px]"
      style="--blob-color: #a855f7; background: radial-gradient(circle, #a855f7, transparent 65%)"
    />

    <div
      class="gradient-blob absolute -right-16 bottom-[20%] h-[500px] w-[500px] rounded-full opacity-35 blur-[100px]"
      style="--blob-color: #3b82f6; background: radial-gradient(circle, #3b82f6, transparent 65%)"
    />

    <div
      class="gradient-blob absolute left-[40%] top-[30%] h-[450px] w-[450px] rounded-full opacity-30 blur-[110px]"
      style="--blob-color: #818cf8; background: radial-gradient(circle, #818cf8, transparent 65%)"
    />
  </div>
</template>
