<script setup lang="ts">
import { gsap } from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'
import { MapPin, Search, Star, Camera, CheckCircle, ArrowLeft } from 'lucide-vue-next'

const pageRef = ref<HTMLElement>()

const beneficios = [
  'Criação ou otimização completa da ficha no Google Meu Negócio',
  'Estratégia de palavras-chave locais para aparecer nas buscas certas',
  'Gestão ativa de avaliações e respostas profissionais',
  'Upload de fotos profissionais e atualizações constantes',
  'Monitoramento de posição no Google Maps e buscas locais',
  'Relatórios mensais de visibilidade e interações',
]

const etapas = [
  { numero: '01', titulo: 'Auditoria da Ficha', descricao: 'Analisamos sua presença atual no Google e identificamos todas as oportunidades de melhoria.', icon: Search },
  { numero: '02', titulo: 'Otimização Completa', descricao: 'Atualizamos cada detalhe: categorias, descrição, horários, fotos, atributos e palavras-chave.', icon: MapPin },
  { numero: '03', titulo: 'Gestão de Avaliações', descricao: 'Criamos uma estratégia para conquistar avaliações positivas e respondemos cada uma delas profissionalmente.', icon: Star },
  { numero: '04', titulo: 'Conteúdo Visual', descricao: 'Publicamos fotos e posts regularmente para manter sua ficha ativa e atrativa para novos clientes.', icon: Camera },
]

onMounted(() => {
  if (import.meta.server) return
  gsap.registerPlugin(ScrollTrigger)

  if (pageRef.value) {
    gsap.from(pageRef.value.querySelectorAll('.animate-in'), {
      opacity: 0, y: 40, duration: 0.7, stagger: 0.12, ease: 'power3.out', delay: 0.2,
    })
    gsap.from(pageRef.value.querySelectorAll('.animate-scroll'), {
      opacity: 0, y: 40, duration: 0.7, stagger: 0.1, ease: 'power3.out',
      scrollTrigger: { trigger: '.animate-scroll', start: 'top 85%' },
    })
  }
})

useHead({ title: 'Presença Local Profissional - Google Meu Negócio | Escala Digital' })
</script>

<template>
  <div ref="pageRef">
    <section class="pb-20 pt-32 md:pt-40">
      <div class="mx-auto max-w-7xl px-6 lg:px-10">
        <NuxtLink to="/" class="animate-in mb-8 inline-flex items-center gap-2 text-sm font-light text-white/40 transition-colors hover:text-white">
          <ArrowLeft :size="16" :stroke-width="1.5" />
          Voltar para Home
        </NuxtLink>

        <div class="grid items-start gap-12 lg:grid-cols-2 lg:gap-20">
          <div>
            <div class="animate-in mb-6 flex items-center gap-3">
              <div class="flex h-12 w-12 items-center justify-center rounded-xl border border-white/10 bg-white/5">
                <MapPin :size="24" :stroke-width="1.5" class="text-white" />
              </div>
              <p class="text-xs font-medium uppercase tracking-[0.25em] text-white/40">Google Meu Negócio</p>
            </div>

            <h1 class="animate-in text-3xl font-extralight leading-tight tracking-tight text-white md:text-5xl lg:text-6xl">
              Presença Local <span class="font-medium">Profissional</span>
            </h1>

            <p class="animate-in mt-6 max-w-lg text-lg font-light leading-relaxed text-white/50">
              Otimização completa da ficha da sua empresa no Google. Apareça no topo das buscas locais e no Google Maps quando os clientes procurarem pelos seus serviços na sua região.
            </p>

            <p class="animate-in mt-4 text-base font-light italic text-white/35">
              "Seja encontrado primeiro quando alguém procurar seus serviços na sua cidade."
            </p>

            <div class="animate-in mt-8">
              <WhatsAppCta mensagem="Olá! Tenho interesse em melhorar minha presença no Google Meu Negócio. Gostaria de saber mais!" size="lg" />
            </div>
          </div>

          <div class="animate-in rounded-2xl border border-white/[0.08] bg-white/[0.03] p-8 backdrop-blur-sm md:p-10">
            <h3 class="mb-6 text-lg font-medium text-white">O que está incluso</h3>
            <ul class="space-y-4">
              <li v-for="beneficio in beneficios" :key="beneficio" class="flex items-start gap-3">
                <CheckCircle :size="18" :stroke-width="1.5" class="mt-0.5 shrink-0 text-[#25D366]" />
                <span class="text-sm font-light leading-relaxed text-white/60">{{ beneficio }}</span>
              </li>
            </ul>
          </div>
        </div>
      </div>
    </section>

    <section class="py-24">
      <div class="mx-auto max-w-7xl px-6 lg:px-10">
        <div class="mb-16">
          <p class="mb-4 text-sm font-medium uppercase tracking-[0.25em] text-white/40">Passo a passo</p>
          <h2 class="text-3xl font-extralight tracking-tight text-white md:text-4xl">
            Como <span class="font-medium">funciona</span>
          </h2>
        </div>

        <div class="grid grid-cols-1 gap-6 md:grid-cols-2 lg:grid-cols-4">
          <div v-for="etapa in etapas" :key="etapa.numero" class="animate-scroll rounded-2xl border border-white/[0.08] bg-white/[0.03] p-8 backdrop-blur-sm">
            <span class="text-3xl font-extralight text-white/40">{{ etapa.numero }}</span>
            <div class="mt-4 mb-3 flex h-10 w-10 items-center justify-center rounded-lg border border-white/10 bg-white/5">
              <component :is="etapa.icon" :size="20" :stroke-width="1.5" class="text-white/70" />
            </div>
            <h3 class="mb-2 text-base font-medium text-white">{{ etapa.titulo }}</h3>
            <p class="text-sm font-light leading-relaxed text-white/45">{{ etapa.descricao }}</p>
          </div>
        </div>
      </div>
    </section>

    <section class="py-24">
      <div class="mx-auto max-w-7xl px-6 lg:px-10">
        <div class="rounded-2xl border border-white/[0.08] bg-white/[0.03] p-10 text-center backdrop-blur-sm md:p-16">
          <h2 class="text-2xl font-extralight tracking-tight text-white md:text-4xl">
            Domine as <span class="font-medium">buscas locais</span>
          </h2>
          <p class="mx-auto mt-4 max-w-lg text-base font-light text-white/50">
            Faça sua empresa aparecer primeiro quando clientes da sua região procurarem pelos seus serviços.
          </p>
          <div class="mt-8">
            <WhatsAppCta mensagem="Olá! Quero aparecer no topo das buscas locais. Podemos conversar?" size="lg" />
          </div>
        </div>
      </div>
    </section>
  </div>
</template>
