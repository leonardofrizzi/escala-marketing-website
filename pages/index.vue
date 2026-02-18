<script setup lang="ts">
import { gsap } from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'
import { Target, MapPin, Video, Globe, ArrowRight, TrendingUp, Users, Zap, CheckCircle, ChevronDown } from 'lucide-vue-next'

const servicos = [
  {
    icon: Target,
    titulo: 'Gestão de Tráfego Pago',
    subtitulo: 'Google Ads & Meta Ads',
    descricao: 'Estratégias personalizadas de anúncios no Google, Instagram e Facebook para atrair clientes prontos para comprar. Foco total em ROI e escala de vendas.',
    itens: ['Campanhas no Google Ads e Meta Ads', 'Segmentação avançada de público', 'Otimização contínua de resultados', 'Relatórios transparentes de performance'],
    href: '/servicos/trafego-pago',
  },
  {
    icon: MapPin,
    titulo: 'Presença Local Profissional',
    subtitulo: 'Google Meu Negócio',
    descricao: 'Otimização completa da ficha da sua empresa no Google. Apareça no topo das buscas locais e no Google Maps quando clientes procurarem seus serviços.',
    itens: ['Otimização de ficha no Google', 'Gestão de avaliações e reputação', 'Posicionamento no Google Maps', 'Fotos e informações profissionais'],
    href: '/servicos/presenca-local',
  },
  {
    icon: Video,
    titulo: 'Criativos de Alta Conversão',
    subtitulo: 'Produção Audiovisual',
    descricao: 'Não fazemos apenas posts, fazemos anúncios que vendem. Vídeos narrados, edições dinâmicas e fotografias profissionais que prendem a atenção em segundos.',
    itens: ['Vídeos narrados e editados', 'Fotografias profissionais', 'Design para redes sociais', 'Edições dinâmicas para anúncios'],
    href: '/servicos/criativos',
  },
  {
    icon: Globe,
    titulo: 'Sites e Landing Pages',
    subtitulo: 'Desenvolvimento Web',
    descricao: 'Criação de sites profissionais com foco em conversão e SEO. Páginas rápidas, seguras e otimizadas para transformar visitantes em compradores.',
    itens: ['Sites responsivos e rápidos', 'Landing pages de alta conversão', 'Otimização para SEO', 'Design moderno e profissional'],
    href: '/servicos/desenvolvimento-web',
  },
]

const diferenciais = [
  { titulo: 'ROI em Foco', descricao: 'Cada real investido é rastreado para garantir retorno máximo', icon: TrendingUp },
  { titulo: 'Atendimento Próximo', descricao: 'Comunicação direta e transparente em cada etapa', icon: Users },
  { titulo: 'Resultados Rápidos', descricao: 'Estratégias ágeis para você ver os primeiros resultados logo', icon: Zap },
]

const faqs = [
  {
    pergunta: 'Quanto tempo leva para ver resultados com tráfego pago?',
    resposta: 'Os primeiros resultados costumam aparecer nos primeiros 7 a 14 dias de campanha. Porém, a otimização contínua nas primeiras semanas é o que garante resultados consistentes e escaláveis a médio e longo prazo.',
  },
  {
    pergunta: 'Preciso ter um site para anunciar no Google ou Instagram?',
    resposta: 'Não necessariamente. Podemos direcionar os anúncios para o WhatsApp, Instagram ou uma landing page que criamos para você. Porém, ter um site profissional aumenta muito a credibilidade e a taxa de conversão.',
  },
  {
    pergunta: 'Qual o investimento mínimo em anúncios?',
    resposta: 'O investimento em mídia (o valor pago ao Google ou Meta) depende do seu mercado e objetivos. Trabalhamos com clientes a partir de R$ 1.000/mês em mídia, além do valor da gestão. Em uma conversa, definimos o ideal para seu caso.',
  },
  {
    pergunta: 'Vocês criam o conteúdo dos anúncios?',
    resposta: 'Sim! Cuidamos de tudo: roteiro, gravação, edição de vídeo, design de peças e copywriting. Você não precisa se preocupar com a parte criativa — entregamos anúncios prontos para rodar.',
  },
  {
    pergunta: 'Como funciona o acompanhamento dos resultados?',
    resposta: 'Enviamos relatórios semanais e mensais com todas as métricas importantes: cliques, conversões, custo por lead, ROI e mais. Além disso, você tem acesso direto à nossa equipe pelo WhatsApp para tirar dúvidas a qualquer momento.',
  },
  {
    pergunta: 'Trabalham com contrato de fidelidade?',
    resposta: 'Não. Trabalhamos com planos mensais sem fidelidade. Acreditamos que os resultados devem falar por si — você fica porque quer, não porque é obrigado.',
  },
]

const faqAberto = ref<number | null>(null)

function toggleFaq(index: number) {
  faqAberto.value = faqAberto.value === index ? null : index
}

onMounted(() => {
  if (import.meta.server) return
  gsap.registerPlugin(ScrollTrigger)

  // hero - sem ScrollTrigger, anima direto na entrada
  gsap.fromTo('.hero-animate',
    { opacity: 0, y: 30 },
    { opacity: 1, y: 0, duration: 0.7, stagger: 0.12, ease: 'power3.out', delay: 0.2 },
  )

  // diferenciais e cards - cada um com seu próprio ScrollTrigger
  document.querySelectorAll('.scroll-reveal').forEach((el, i) => {
    gsap.fromTo(el,
      { opacity: 0, y: 40 },
      {
        opacity: 1,
        y: 0,
        duration: 0.6,
        delay: i * 0.08,
        ease: 'power3.out',
        scrollTrigger: {
          trigger: el,
          start: 'top 90%',
        },
      },
    )
  })
})
</script>

<template>
  <div>
    <!-- Hero -->
    <section class="flex min-h-screen items-center pt-20">
      <div class="mx-auto max-w-7xl px-6 lg:px-10">
        <p class="hero-animate mb-6 text-sm font-medium uppercase tracking-[0.25em] text-white/40">
          Agência de Marketing Digital
        </p>

        <h1 class="hero-animate max-w-3xl text-3xl font-extralight leading-tight tracking-tight text-white md:text-5xl lg:text-6xl">
          Sua empresa no topo do
          <span class="font-medium">Google</span> e das
          <span class="font-medium">Redes Sociais</span> com anúncios que vendem de verdade.
        </h1>

        <p class="hero-animate mt-6 max-w-2xl text-lg font-light leading-relaxed text-white/50 md:text-xl">
          Estratégias de tráfego pago, criativos e presença digital que transformam cliques em clientes reais.
        </p>

        <div class="hero-animate mt-10 flex flex-wrap items-center gap-4">
          <NuxtLink
            to="/#contato"
            class="inline-flex items-center gap-2 rounded-full bg-white px-5 py-3 text-sm font-medium tracking-wide text-dark transition-all duration-200 hover:bg-white/90"
          >
            <svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" viewBox="0 0 24 24" fill="currentColor"><path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 01-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 01-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 012.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0012.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 005.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 00-3.48-8.413z"/></svg>
            Solicitar Orçamento Personalizado
          </NuxtLink>

          <NuxtLink
            to="/#servicos"
            class="inline-flex items-center gap-2 rounded-full border border-white/10 px-8 py-3.5 text-sm font-light tracking-wide text-white/70 transition-all duration-200 hover:border-white/20 hover:text-white"
          >
            Nossos Serviços
            <ArrowRight :size="16" :stroke-width="1.5" />
          </NuxtLink>
        </div>
      </div>
    </section>

    <!-- Diferenciais -->
    <section class="py-20">
      <div class="mx-auto max-w-7xl px-6 lg:px-10">
        <div class="grid grid-cols-1 gap-px overflow-hidden rounded-2xl border border-white/10 md:grid-cols-3">
          <div
            v-for="item in diferenciais"
            :key="item.titulo"
            class="scroll-reveal bg-white/[0.04] p-8 backdrop-blur-sm md:p-10"
          >
            <div class="mb-4 flex h-12 w-12 items-center justify-center rounded-xl border border-white/10 bg-white/5">
              <component :is="item.icon" :size="22" :stroke-width="1.5" class="text-white" />
            </div>
            <p class="text-lg font-medium tracking-tight text-white">{{ item.titulo }}</p>
            <p class="mt-2 text-sm font-light leading-relaxed text-white/50">{{ item.descricao }}</p>
          </div>
        </div>
      </div>
    </section>

    <!-- Serviços -->
    <section id="servicos" class="py-24">
      <div class="mx-auto max-w-7xl px-6 lg:px-10">
        <div class="mb-16">
          <p class="mb-4 text-sm font-medium uppercase tracking-[0.25em] text-white/40">
            O que fazemos
          </p>
          <h2 class="text-3xl font-extralight tracking-tight text-white md:text-5xl">
            Nossos <span class="font-medium">serviços</span>
          </h2>
        </div>

        <div class="grid grid-cols-1 gap-6 md:grid-cols-2">
          <div
            v-for="servico in servicos"
            :key="servico.titulo"
            class="scroll-reveal group rounded-2xl border border-white/[0.08] bg-white/[0.03] p-8 backdrop-blur-sm transition-all duration-300 hover:border-white/15 hover:bg-white/[0.05] md:p-10"
          >
            <div class="mb-6 flex items-center gap-4">
              <div class="flex h-12 w-12 shrink-0 items-center justify-center rounded-xl border border-white/10 bg-white/5">
                <component :is="servico.icon" :size="24" :stroke-width="1.5" class="text-white" />
              </div>
              <div>
                <p class="text-xs font-medium uppercase tracking-[0.2em] text-white/30">{{ servico.subtitulo }}</p>
                <h3 class="text-lg font-medium tracking-tight text-white md:text-xl">{{ servico.titulo }}</h3>
              </div>
            </div>

            <p class="mb-6 text-sm font-light leading-relaxed text-white/50">
              {{ servico.descricao }}
            </p>

            <ul class="mb-8 space-y-3">
              <li v-for="item in servico.itens" :key="item" class="flex items-center gap-3 text-sm font-light text-white/60">
                <CheckCircle :size="16" :stroke-width="1.5" class="shrink-0 text-[#25D366]" />
                {{ item }}
              </li>
            </ul>

            <NuxtLink
              :to="servico.href"
              class="inline-flex items-center gap-2 text-sm font-medium text-white/70 transition-colors duration-200 group-hover:text-white"
            >
              Saiba mais
              <ArrowRight :size="14" :stroke-width="1.5" class="transition-transform duration-200 group-hover:translate-x-1" />
            </NuxtLink>
          </div>
        </div>
      </div>
    </section>

    <!-- Sobre Nós -->
    <section id="sobre" class="py-24">
      <div class="mx-auto max-w-7xl px-6 lg:px-10">
        <div class="scroll-reveal mx-auto max-w-3xl text-center">
          <p class="mb-4 text-sm font-medium uppercase tracking-[0.25em] text-white/40">
            Sobre nós
          </p>
          <h2 class="text-3xl font-extralight tracking-tight text-white md:text-5xl">
            Quem é a <span class="font-medium">Escala Marketing</span>
          </h2>
          <p class="mt-6 text-lg font-light leading-relaxed text-white/50">
            Somos uma agência de marketing digital com um objetivo claro: escalar os resultados do seu negócio. Acreditamos que toda empresa merece uma presença digital forte, estratégias inteligentes e resultados reais — não métricas de vaidade.
          </p>
          <p class="mt-4 text-lg font-light leading-relaxed text-white/50">
            Combinamos tráfego pago, criativos de alta conversão, presença local e desenvolvimento web para criar um ecossistema completo que transforma investimento em vendas. Nosso compromisso é com o seu crescimento.
          </p>
          <div class="mt-8">
            <NuxtLink
              to="/#contato"
              class="inline-flex items-center gap-2 rounded-full bg-white px-8 py-3.5 text-sm font-medium tracking-wide text-dark transition-all duration-200 hover:bg-white/90"
            >
              <svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" viewBox="0 0 24 24" fill="currentColor"><path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 01-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 01-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 012.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0012.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 005.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 00-3.48-8.413z"/></svg>
              Fale Conosco
            </NuxtLink>
          </div>
        </div>
      </div>
    </section>

    <!-- Contato -->
    <section id="contato" class="py-24">
      <div class="mx-auto max-w-7xl px-6 lg:px-10">
        <div class="scroll-reveal mb-16 text-center">
          <p class="mb-4 text-sm font-medium uppercase tracking-[0.25em] text-white/40">
            Contato
          </p>
          <h2 class="text-3xl font-extralight tracking-tight text-white md:text-5xl">
            Vamos <span class="font-medium">conversar</span>?
          </h2>
        </div>

        <div class="scroll-reveal grid grid-cols-1 gap-4 md:grid-cols-3">
          <!-- WhatsApp -->
          <a
            href="https://wa.me/5516997451992?text=Ol%C3%A1!%20Gostaria%20de%20saber%20mais%20sobre%20os%20servi%C3%A7os%20da%20Escala%20Marketing."
            target="_blank"
            rel="noopener noreferrer"
            class="group relative overflow-hidden rounded-2xl border border-white/[0.08] p-8 transition-all duration-300 hover:border-[#25D366]/30 md:p-10"
          >
            <div class="absolute inset-0 bg-gradient-to-br from-[#25D366]/10 to-transparent opacity-0 transition-opacity duration-300 group-hover:opacity-100" />
            <div class="relative">
              <div class="mb-5 flex h-14 w-14 items-center justify-center rounded-2xl border border-[#25D366]/20 bg-[#25D366]/10">
                <svg xmlns="http://www.w3.org/2000/svg" width="26" height="26" viewBox="0 0 24 24" fill="#25D366"><path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 01-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 01-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 012.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0012.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 005.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 00-3.48-8.413z"/></svg>
              </div>
              <h3 class="mb-2 text-lg font-medium text-white">WhatsApp</h3>
              <p class="text-sm font-light text-white/50">Resposta rápida e direta</p>
              <p class="mt-3 text-sm font-light text-[#25D366] transition-colors group-hover:text-[#25D366]">(16) 99745-1992</p>
            </div>
          </a>

          <!-- Instagram -->
          <a
            href="https://www.instagram.com/escalamarketing2/"
            target="_blank"
            rel="noopener noreferrer"
            class="group relative overflow-hidden rounded-2xl border border-white/[0.08] p-8 transition-all duration-300 hover:border-pink-500/30 md:p-10"
          >
            <div class="absolute inset-0 bg-gradient-to-br from-pink-500/10 via-purple-500/5 to-transparent opacity-0 transition-opacity duration-300 group-hover:opacity-100" />
            <div class="relative">
              <div class="mb-5 flex h-14 w-14 items-center justify-center rounded-2xl border border-pink-500/20 bg-pink-500/10">
                <svg xmlns="http://www.w3.org/2000/svg" width="26" height="26" viewBox="0 0 24 24" fill="none" stroke="#ec4899" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"><rect width="20" height="20" x="2" y="2" rx="5" ry="5"/><path d="M16 11.37A4 4 0 1 1 12.63 8 4 4 0 0 1 16 11.37z"/><line x1="17.5" x2="17.51" y1="6.5" y2="6.5"/></svg>
              </div>
              <h3 class="mb-2 text-lg font-medium text-white">Instagram</h3>
              <p class="text-sm font-light text-white/50">Acompanhe nosso conteúdo</p>
              <p class="mt-3 text-sm font-light text-pink-400 transition-colors group-hover:text-pink-400">@escalamarketing2</p>
            </div>
          </a>

          <!-- Email -->
          <a
            href="mailto:contato@escalamarketing.com"
            class="group relative overflow-hidden rounded-2xl border border-white/[0.08] p-8 transition-all duration-300 hover:border-blue-400/30 md:p-10"
          >
            <div class="absolute inset-0 bg-gradient-to-br from-blue-400/10 to-transparent opacity-0 transition-opacity duration-300 group-hover:opacity-100" />
            <div class="relative">
              <div class="mb-5 flex h-14 w-14 items-center justify-center rounded-2xl border border-blue-400/20 bg-blue-400/10">
                <svg xmlns="http://www.w3.org/2000/svg" width="26" height="26" viewBox="0 0 24 24" fill="none" stroke="#60a5fa" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"><rect width="20" height="16" x="2" y="4" rx="2"/><path d="m22 7-8.97 5.7a1.94 1.94 0 0 1-2.06 0L2 7"/></svg>
              </div>
              <h3 class="mb-2 text-lg font-medium text-white">E-mail</h3>
              <p class="text-sm font-light text-white/50">Para propostas e parcerias</p>
              <p class="mt-3 text-sm font-light text-blue-400 transition-colors group-hover:text-blue-400">contato@escalamarketing.com</p>
            </div>
          </a>
        </div>
      </div>
    </section>

    <!-- FAQ -->
    <section id="faq" class="py-24">
      <div class="mx-auto max-w-7xl px-6 lg:px-10">
        <div class="scroll-reveal mb-16 text-center">
          <p class="mb-4 text-sm font-medium uppercase tracking-[0.25em] text-white/40">
            FAQ
          </p>
          <h2 class="text-3xl font-extralight tracking-tight text-white md:text-5xl">
            Perguntas <span class="font-medium">frequentes</span>
          </h2>
        </div>

        <div class="scroll-reveal space-y-3">
          <div
            v-for="(faq, i) in faqs"
            :key="i"
            class="rounded-2xl border transition-all duration-300"
            :class="faqAberto === i ? 'border-white/15 bg-white/[0.05]' : 'border-white/[0.08] bg-white/[0.02]'"
          >
            <button
              class="flex w-full items-center justify-between gap-4 p-6 text-left md:p-7"
              @click="toggleFaq(i)"
            >
              <span class="text-sm font-medium leading-relaxed text-white md:text-base">{{ faq.pergunta }}</span>
              <ChevronDown
                :size="20"
                :stroke-width="1.5"
                class="shrink-0 text-white/40 transition-transform duration-300"
                :class="faqAberto === i ? 'rotate-180' : ''"
              />
            </button>
            <Transition
              enter-active-class="transition-all duration-300 ease-out"
              enter-from-class="max-h-0 opacity-0"
              enter-to-class="max-h-40 opacity-100"
              leave-active-class="transition-all duration-200 ease-in"
              leave-from-class="max-h-40 opacity-100"
              leave-to-class="max-h-0 opacity-0"
            >
              <div v-show="faqAberto === i" class="overflow-hidden">
                <p class="px-6 pb-6 text-sm font-light leading-relaxed text-white/50 md:px-7 md:pb-7">
                  {{ faq.resposta }}
                </p>
              </div>
            </Transition>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>
