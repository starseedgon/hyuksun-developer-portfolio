<script setup lang="ts">
import { onMounted, ref } from 'vue'

const profile = {
  email: 'monad.gon@example.com',
  github: 'https://github.com/YOUR_GITHUB_ID',
}
const navOpen = ref(false)
const currentYear = new Date().getFullYear()

const projects = [
  {
    number: '01', category: 'FMS · Web Platform', title: '통합 시설 알람 모니터링',
    description: '다수 테넌트의 소방·가스·설비 알람을 실시간으로 수집하고, SOP와 방송 기능까지 하나의 운영 화면으로 연결했습니다.',
    impact: '20,000 사용자 규모를 고려한 멀티테넌트 설계',
    stack: ['Vue 3', 'Spring Boot', 'PostgreSQL', 'Keycloak'],
  },
  {
    number: '02', category: 'AI · Knowledge System', title: '소방 법령 RAG 시스템',
    description: '복잡한 소방 관계 법령을 문서·조문·별표 단위로 구조화하고, 근거를 찾을 수 있는 로컬 LLM 기반 질의응답 시스템을 설계했습니다.',
    impact: 'pgVector 기반 1,024차원 의미 검색',
    stack: ['Python', 'Ollama', 'BGE-M3', 'pgVector'],
  },
  {
    number: '03', category: 'IoT · System Integration', title: '현장 설비 통신 및 제어',
    description: 'PLC, 조명 제어기, 소방 수신기 등 서로 다른 현장 장비의 데이터를 안정적으로 수집하고 제어하는 연동 모듈을 개발했습니다.',
    impact: 'RS-232/485 · Modbus · TCP 프로토콜 통합',
    stack: ['Python', 'MELSEC', 'Modbus', 'Serial/TCP'],
  },
  {
    number: '04', category: 'Video · Realtime', title: 'CCTV 웹 스트리밍 연동',
    description: 'RTSP 영상을 웹에서 낮은 지연으로 확인할 수 있도록 WebRTC 변환 파이프라인과 다분할 모니터링 화면을 구성했습니다.',
    impact: '4·9·16분할 실시간 영상 모니터링',
    stack: ['MediaMTX', 'WebRTC', 'Nginx', 'Vue'],
  },
]

const skills = [
  { group: 'Frontend', items: ['Vue 3', 'TypeScript', 'Vite', 'Vuetify'] },
  { group: 'Backend', items: ['Java 17', 'Spring Boot', 'REST API', 'WebSocket'] },
  { group: 'Data & Auth', items: ['PostgreSQL', 'pgVector', 'Keycloak', 'RAG'] },
  { group: 'Infrastructure', items: ['Nginx', 'Docker', 'Jenkins', 'Linux'] },
  { group: 'Field Integration', items: ['PLC', 'Modbus', 'RS-232/485', 'TCP/IP'] },
]

const closeNav = () => { navOpen.value = false }
onMounted(() => {
  const observer = new IntersectionObserver(
    entries => entries.forEach(entry => entry.isIntersecting && entry.target.classList.add('is-visible')),
    { threshold: 0.14 },
  )
  document.querySelectorAll('.reveal').forEach(el => observer.observe(el))
})
</script>

<template>
  <div class="site-shell">
    <header class="topbar">
      <a class="brand" href="#top" aria-label="맨 위로">KHS<span>.</span></a>
      <button class="menu-button" type="button" :aria-expanded="navOpen" aria-label="메뉴 열기" @click="navOpen = !navOpen"><span></span><span></span></button>
      <nav :class="['nav', { open: navOpen }]" aria-label="주요 메뉴">
        <a href="#about" @click="closeNav">소개</a><a href="#projects" @click="closeNav">프로젝트</a>
        <a href="#skills" @click="closeNav">기술</a><a href="#contact" @click="closeNav">연락처</a>
      </nav>
    </header>

    <main id="top">
      <section class="hero">
        <div class="hero-grid" aria-hidden="true"></div>
        <div class="hero-copy reveal">
          <p class="eyebrow"><span class="status-dot"></span> System Developer · Seoul, Korea</p>
          <h1>복잡한 현장 시스템을<br><em>안정적인 서비스로</em><br>연결합니다.</h1>
          <p class="hero-description">안녕하세요, 권혁선입니다. 시설관리·소방·자동제어 분야의 깊은 현장 이해를 바탕으로 웹 서비스부터 장비 통신까지 설계하고 운영합니다.</p>
          <div class="hero-actions">
            <a class="button primary" href="#projects">프로젝트 보기 <span>↘</span></a>
            <a class="button ghost" :href="`mailto:${profile.email}`">이메일 보내기</a>
          </div>
        </div>
        <div class="hero-visual reveal" aria-label="개발 분야 요약">
          <div class="orbit orbit-one"></div><div class="orbit orbit-two"></div>
          <div class="core"><span>FIELD</span><strong>×</strong><span>CODE</span></div>
          <span class="orbit-label label-web">WEB</span><span class="orbit-label label-data">DATA</span><span class="orbit-label label-iot">IoT</span>
        </div>
        <div class="scroll-note">SCROLL TO EXPLORE <span>↓</span></div>
      </section>

      <section id="about" class="section about reveal">
        <p class="section-index">01 / ABOUT</p>
        <div class="about-copy">
          <h2>코드와 현장 사이의<br>간격을 줄입니다.</h2>
          <div class="about-detail">
            <p>좋은 시스템은 화면 안에서만 완성되지 않습니다. 센서와 제어기, 네트워크와 데이터베이스, 그리고 실제 운영자의 업무 흐름까지 함께 이해해야 합니다.</p>
            <p>저는 개발과 운영을 분리하지 않고, 오래 안정적으로 사용할 수 있는 구조를 고민합니다. 문제의 원인을 끝까지 추적하고 기술을 현실적인 해결책으로 바꾸는 것이 저의 강점입니다.</p>
          </div>
        </div>
        <div class="principles">
          <article><span>01</span><h3>현장 중심</h3><p>실제 사용자의 업무와 장비 환경에서 출발합니다.</p></article>
          <article><span>02</span><h3>안정성 우선</h3><p>장시간 운영과 장애 복구까지 고려해 설계합니다.</p></article>
          <article><span>03</span><h3>끝까지 연결</h3><p>프론트엔드부터 현장 프로토콜까지 연결합니다.</p></article>
        </div>
      </section>

      <section id="projects" class="section projects">
        <div class="section-heading reveal"><p class="section-index">02 / SELECTED WORK</p><h2>주요 프로젝트</h2><p>현장에서 작동하고 운영으로 증명된 경험입니다.</p></div>
        <div class="project-list">
          <article v-for="project in projects" :key="project.number" class="project-card reveal">
            <div class="project-number">{{ project.number }}</div>
            <div class="project-main"><p class="project-category">{{ project.category }}</p><h3>{{ project.title }}</h3><p>{{ project.description }}</p><strong>{{ project.impact }}</strong></div>
            <ul class="tags"><li v-for="item in project.stack" :key="item">{{ item }}</li></ul>
          </article>
        </div>
      </section>

      <section id="skills" class="section skills reveal">
        <div class="section-heading"><p class="section-index">03 / CAPABILITIES</p><h2>기술 스택</h2></div>
        <div class="skill-grid">
          <article v-for="skill in skills" :key="skill.group"><h3>{{ skill.group }}</h3><ul><li v-for="item in skill.items" :key="item">{{ item }}</li></ul></article>
        </div>
      </section>

      <section id="contact" class="contact reveal">
        <p class="section-index">04 / CONTACT</p><h2>함께 해결할 문제가<br>있으신가요?</h2>
        <p>새로운 프로젝트, 시스템 연동 또는 기술적인 대화는 언제든 환영합니다.</p>
        <div class="contact-links">
          <a :href="`mailto:${profile.email}`">{{ profile.email }} <span>↗</span></a>
          <a :href="profile.github" target="_blank" rel="noreferrer">GitHub <span>↗</span></a>
        </div>
      </section>
    </main>
    <footer><a class="brand" href="#top">KHS<span>.</span></a><p>© {{ currentYear }} Kwon Hyuksun. Built with Vue 3.</p><a href="#top">맨 위로 ↑</a></footer>
  </div>
</template>
