<script setup lang="ts">
import { gsap } from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'
import { Target, BarChart3, MousePointerClick, LineChart, CheckCircle, ArrowLeft } from 'lucide-vue-next'

const pageRef = ref<HTMLElement>()

const beneficios = [
  'Campanhas otimizadas no Google Ads (Pesquisa, Display e YouTube)',
  'Anúncios no Instagram e Facebook com segmentação avançada',
  'Remarketing para quem já visitou seu site ou interagiu com sua marca',
  'Testes A/B constantes para encontrar os melhores anúncios',
  'Relatórios semanais e mensais com métricas claras',
  'Otimização diária de orçamento para maximizar o ROI',
]

const etapas = [
  { numero: '01', titulo: 'Análise do Negócio', descricao: 'Entendemos seu produto, público-alvo, concorrência e objetivos para montar a estratégia ideal.', icon: Target },
  { numero: '02', titulo: 'Criação das Campanhas', descricao: 'Estruturamos campanhas com segmentação precisa, criativos persuasivos e páginas de destino otimizadas.', icon: MousePointerClick },
  { numero: '03', titulo: 'Otimização Contínua', descricao: 'Monitoramos diariamente os resultados, ajustando lances, públicos e criativos para melhor performance.', icon: BarChart3 },
  { numero: '04', titulo: 'Escala de Resultados', descricao: 'Com os dados validados, escalamos o investimento de forma inteligente para multiplicar seus resultados.', icon: LineChart },
]

onMounted(() => {
  if (import.meta.server) return
  gsap.registerPlugin(ScrollTrigger)

  if (pageRef.value) {
    gsap.from(pageRef.value.querySelectorAll('.animate-in'), {
      opacity: 0,
      y: 40,
      duration: 0.7,
      stagger: 0.12,
      ease: 'power3.out',
      delay: 0.2,
    })

    gsap.from(pageRef.value.querySelectorAll('.animate-scroll'), {
      opacity: 0,
      y: 40,
      duration: 0.7,
      stagger: 0.1,
      ease: 'power3.out',
      scrollTrigger: { trigger: '.animate-scroll', start: 'top 85%' },
    })
  }
})

useHead({ title: 'Gestão de Tráfego Pago - Google Ads & Meta Ads | Escala Marketing' })
</script>

<template>
  <div ref="pageRef">
    <!-- Hero -->
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
                <Target :size="24" :stroke-width="1.5" class="text-white" />
              </div>
              <p class="text-xs font-medium uppercase tracking-[0.25em] text-white/40">Google Ads & Meta Ads</p>
            </div>

            <h1 class="animate-in text-3xl font-extralight leading-tight tracking-tight text-white md:text-5xl lg:text-6xl">
              Gestão de <span class="font-medium">Tráfego Pago</span>
            </h1>

            <p class="animate-in mt-6 max-w-lg text-lg font-light leading-relaxed text-white/50">
              Estratégias personalizadas de anúncios no Google, Instagram e Facebook para atrair clientes prontos para comprar. Foco total em ROI e escala de vendas.
            </p>

            <p class="animate-in mt-4 text-base font-light italic text-white/35">
              "Anúncios segmentados para o público certo, na hora certa."
            </p>

            <div class="animate-in mt-8">
              <WhatsAppCta mensagem="Olá! Tenho interesse em Gestão de Tráfego Pago. Gostaria de saber mais!" size="lg" />
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

    <!-- Como funciona -->
    <section class="py-24">
      <div class="mx-auto max-w-7xl px-6 lg:px-10">
        <div class="mb-16">
          <p class="mb-4 text-sm font-medium uppercase tracking-[0.25em] text-white/40">Passo a passo</p>
          <h2 class="text-3xl font-extralight tracking-tight text-white md:text-4xl">
            Como <span class="font-medium">funciona</span>
          </h2>
        </div>

        <div class="grid grid-cols-1 gap-6 md:grid-cols-2 lg:grid-cols-4">
          <div
            v-for="etapa in etapas"
            :key="etapa.numero"
            class="animate-scroll rounded-2xl border border-white/[0.08] bg-white/[0.03] p-8 backdrop-blur-sm"
          >
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

    <!-- CTA Final -->
    <section class="py-24">
      <div class="mx-auto max-w-7xl px-6 lg:px-10">
        <div class="rounded-2xl border border-white/[0.08] bg-white/[0.03] p-10 text-center backdrop-blur-sm md:p-16">
          <h2 class="text-2xl font-extralight tracking-tight text-white md:text-4xl">
            Pronto para <span class="font-medium">escalar suas vendas</span>?
          </h2>
          <p class="mx-auto mt-4 max-w-lg text-base font-light text-white/50">
            Entre em contato e descubra como o tráfego pago pode transformar os resultados do seu negócio.
          </p>
          <div class="mt-8">
            <WhatsAppCta mensagem="Olá! Quero escalar minhas vendas com tráfego pago. Podemos conversar?" size="lg" />
          </div>
        </div>
      </div>
    </section>
  </div>
</template>
