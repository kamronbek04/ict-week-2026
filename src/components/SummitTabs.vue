<script setup>
import { ref } from 'vue'
import summitCard from '../assets/summit-card.webp'
import summitPhoto from '../assets/summit-photo.webp'

const tabs = [
  { id: 'enterprise', label: 'ENTERPRISE UZBEKISTAN', short: 'ENTERPRISE' },
  { id: 'startup', label: 'STARTUP & VC' },
  { id: 'service', label: 'SERVICE COMPANIES' },
  { id: 'bridge', label: 'GLOBAL BRIDGE' },
  { id: 'gamedev', label: 'GAMEDEV' },
  { id: 'ai', label: 'AI NATIVE' }
]

const content = {
  enterprise: {
    title: 'ENTERPRISE UZBEKISTAN SUMMIT',
    date: 'September 23,2026',
    dateTablet: 'September 22, 2026',
    dateMobile: 'Sep 23, 2026',
    time: '10:00 - 12:00',
    timeTablet: '11:00 - 13:30',
    place: 'CAEx, Hall 1',
    placeTablet: 'CAEx, Main Hall',
    intro: 'Discover Enterprise Uzbekistan — the country’s first dedicated jurisdiction built for global technology business.',
    introTablet: 'Discover Enterprise Uzbekistan — the country’s first International Digital Technologies Center, created specifically for global tech companies, from data centers and AI startups to the tech giants.',
    bullets: [
      'Running on elements of English and Welsh law, it offers a legal environment that locks in the day you enter and remains guaranteed through 2100 — for IT exporters, data centers, startups, and infrastructure and institutional investors alike.',
      'On September 23, Enterprise Uzbekistan takes the stage at ICT Week to open the framework up in person. Meet the people building it, see how it’s structured, and get a first look at what it means to operate inside it.',
      'Join us at CAEx, Main Hall — come see it before everyone else does.'
    ],
    bulletsTablet: [
      'Special legal regime based on English law, with access to an independent commercial court',
      'Full tax exemptions: income tax, profit tax, VAT and customs duties for center participants - until 2100',
      'Sandbox to test and launch new digital products and services'
    ],
    ideal: 'global tech companies, investors, legal and financial advisors, and government officials'
  }
}

const active = ref('enterprise')
const data = () => content[active.value] || content.enterprise
</script>

<template>
  <section id="program" class="summit">
    <div class="panel">
      <div class="tabs" role="tablist">
        <button
          v-for="t in tabs"
          :key="t.id"
          type="button"
          role="tab"
          :aria-selected="active === t.id"
          class="tab"
          :class="{ on: active === t.id }"
          @click="active = t.id"
        >
          <template v-if="t.short">
            <span class="v-dt">{{ t.label }}</span>
            <span class="v-m">{{ t.short }}</span>
          </template>
          <template v-else>{{ t.label }}</template>
        </button>
      </div>
      <h2>{{ data().title }}</h2>
      <div class="meta">
        <span class="meta-item">
          <svg width="18" height="18" viewBox="0 0 18 18" fill="none" aria-hidden="true">
            <rect x="2.2" y="3.2" width="13.6" height="12.6" rx="2" stroke="#84ffc1" stroke-width="1.4" />
            <path d="M2.2 7h13.6M6 1.6v3.2M12 1.6v3.2" stroke="#84ffc1" stroke-width="1.4" stroke-linecap="round" />
          </svg>
          <span class="v-d">{{ data().date }}</span>
          <span class="v-t">{{ data().dateTablet }}</span>
          <span class="v-m">{{ data().dateMobile }}</span>
        </span>
        <span class="meta-item">
          <svg width="18" height="18" viewBox="0 0 18 18" fill="none" aria-hidden="true">
            <circle cx="9" cy="9" r="7" stroke="#84ffc1" stroke-width="1.4" />
            <path d="M9 5.2V9l2.6 1.6" stroke="#84ffc1" stroke-width="1.4" stroke-linecap="round" />
          </svg>
          <span class="v-dm">{{ data().time }}</span>
          <span class="v-t">{{ data().timeTablet }}</span>
        </span>
        <span class="meta-item">
          <svg width="18" height="18" viewBox="0 0 18 18" fill="none" aria-hidden="true">
            <path d="M9 16.5S3.4 11.6 3.4 7.6a5.6 5.6 0 1 1 11.2 0c0 4-5.6 8.9-5.6 8.9z" stroke="#84ffc1" stroke-width="1.4" />
            <circle cx="9" cy="7.6" r="2.1" stroke="#84ffc1" stroke-width="1.4" />
          </svg>
          <span class="v-dm">{{ data().place }}</span>
          <span class="v-t">{{ data().placeTablet }}</span>
        </span>
      </div>
      <div class="body">
        <a href="#register" class="photo-card">
          <img :src="summitCard" alt="" width="420" height="370" loading="lazy" />
          <span class="photo-card-overlay">
            <span class="photo-card-title">Enterprise Uzbekistan Summit</span>
            <span class="photo-card-description">Legally protected testing environment for new business models and frontier technologies.</span>
            <span class="photo-card-cta">Register now <span aria-hidden="true">→</span></span>
          </span>
        </a>
        <img class="photo-plain" :src="summitPhoto" alt="Enterprise Uzbekistan Summit keynote at ICT Week" width="576" height="298" loading="lazy" />
        <div class="info">
          <p class="lead">
            <span class="v-dm">{{ data().intro }}</span>
            <span class="v-t">{{ data().introTablet }}</span>
          </p>
          <ul class="list-dm">
            <li v-for="(b, i) in data().bullets" :key="i">
              <svg width="20" height="20" viewBox="0 0 20 20" fill="none" aria-hidden="true">
                <circle cx="10" cy="10" r="10" fill="#2ecc8f" />
                <path d="M6 10.2l2.6 2.6L14 7.4" stroke="#04130d" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round" />
              </svg>
              <span>{{ b }}</span>
            </li>
          </ul>
          <ul class="list-t">
            <li v-for="(b, i) in data().bulletsTablet" :key="i">
              <svg width="20" height="20" viewBox="0 0 20 20" fill="none" aria-hidden="true">
                <circle cx="10" cy="10" r="10" fill="#2ecc8f" />
                <path d="M6 10.2l2.6 2.6L14 7.4" stroke="#04130d" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round" />
              </svg>
              <span>{{ b }}</span>
            </li>
          </ul>
          <p class="ideal">
            <span class="ideal-bar"></span>
            <span><em>Ideal for:</em> <strong>{{ data().ideal }}</strong></span>
          </p>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.v-t,
.v-m,
.list-t {
  display: none;
}

.summit {
  margin-top: 68px;
}

.panel {
  width: 1280px;
  height: 784px;
  margin-left: 80px;
  padding: 40px 40px 48px;
  border-radius: 24px;
  background: var(--glass-panel);
  box-shadow: var(--glass-shadow);
  -webkit-backdrop-filter: var(--glass-filter);
  backdrop-filter: var(--glass-filter);
}

.tabs {
  display: flex;
  justify-content: center;
  gap: 12px;
}

.tab {
  flex: none;
  height: 44px;
  padding: 0;
  border-radius: 22px;
  border: 1px solid rgba(255, 255, 255, 0.102);
  background: rgba(255, 255, 255, 0.0314);
  -webkit-backdrop-filter: blur(6px);
  backdrop-filter: blur(6px);
  color: #dfe4e4;
  font-size: 14px;
  font-weight: 600;
  letter-spacing: 0.02em;
  white-space: nowrap;
}

.tab:nth-child(1) { width: 258px; }
.tab:nth-child(2) { width: 160px; }
.tab:nth-child(3) { width: 217px; }
.tab:nth-child(4) { width: 171px; }
.tab:nth-child(5) { width: 121px; }
.tab:nth-child(6) { width: 118px; }

.tab.on {
  background: #84ffc1;
  border-color: #84ffc1;
  color: #0b1a14;
}

h2 {
  margin-top: 30px;
  text-align: center;
  font-size: 52px;
  line-height: 1.15;
  font-weight: 700;
  letter-spacing: 0.5px;
  text-transform: uppercase;
}

.meta {
  display: flex;
  align-items: center;
  margin-top: 36px;
  height: 52px;
  border: 1px solid rgba(255, 255, 255, 0.102);
  border-radius: 16px;
  background: rgba(255, 255, 255, 0.0314);
  -webkit-backdrop-filter: blur(6px);
  backdrop-filter: blur(6px);
}

.meta-item {
  flex: 1;
  display: flex;
  align-items: center;
  justify-content: flex-start;
  gap: 10px;
  padding-left: 20px;
  font-size: 14px;
  font-weight: 600;
}

.meta-item + .meta-item {
  border-left: 1px solid rgba(255, 255, 255, 0.12);
  padding-left: 16px;
}

.body {
  display: flex;
  gap: 32px;
  height: 442px;
  margin-top: 32px;
  padding: 35px;
  border: 1px solid rgba(255, 255, 255, 0.102);
  border-radius: 20px;
  background:
    radial-gradient(ellipse 54% 100% at 52% 0%, rgba(132, 255, 193, 0.08), transparent 100%),
    linear-gradient(180deg, rgba(132, 255, 193, 0.02), rgba(132, 255, 193, 0.016)),
    rgba(255, 255, 255, 0.0314);
  box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.035);
  -webkit-backdrop-filter: blur(8px);
  backdrop-filter: blur(8px);
}

.photo-card {
  flex: none;
  position: relative;
  display: block;
  width: 420px;
  height: 370px;
  overflow: hidden;
  border-radius: 12px;
  color: #fff;
  text-decoration: none;
}

.photo-card img {
  display: block;
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition:
    transform 0.3s ease,
    filter 0.3s ease;
}

.photo-card-overlay {
  position: absolute;
  inset: 0;
  display: flex;
  flex-direction: column;
  padding: 24px;
  background: rgba(0, 0, 0, 0.5);
  opacity: 0;
  transition: opacity 0.3s ease;
}

.photo-card-title {
  font-size: 20px;
  line-height: 26px;
  font-weight: 700;
}

.photo-card-description {
  max-width: 350px;
  margin-top: 8px;
  font-size: 14px;
  line-height: 18px;
}

.photo-card-cta {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  align-self: flex-start;
  min-width: 162px;
  height: 46px;
  margin-top: auto;
  padding: 0 20px;
  border-radius: 12px;
  background: #84ffc1;
  color: #071710;
  font-size: 14px;
  line-height: 20px;
  font-weight: 700;
}

.photo-card:hover img,
.photo-card:focus-visible img {
  filter: blur(5px);
  transform: scale(1.04);
}

.photo-card:hover .photo-card-overlay,
.photo-card:focus-visible .photo-card-overlay {
  opacity: 1;
}

.photo-card:focus-visible {
  outline: 2px solid #84ffc1;
  outline-offset: 3px;
}

.photo-plain {
  display: none;
  border-radius: 12px;
  object-fit: cover;
}

.info {
  flex: 1;
  min-width: 0;
  display: flex;
  flex-direction: column;
}

.lead {
  font-size: 16px;
  line-height: 24px;
  font-weight: 600;
}

ul {
  list-style: none;
  margin-top: 48px;
  display: flex;
  flex-direction: column;
  gap: 28px;
}

li {
  display: flex;
  gap: 14px;
  font-size: 14px;
  line-height: 20px;
  color: #d7dcdc;
}

li svg {
  flex: none;
  margin-top: 2px;
}

li:nth-child(3) {
  margin-top: -6px;
}

.ideal {
  display: flex;
  align-items: center;
  gap: 16px;
  height: 78px;
  margin-top: auto;
  padding: 16px;
  border: 1px solid transparent;
  border-radius: 12px;
  background:
    linear-gradient(#15272a, #15272a) padding-box,
    linear-gradient(90deg, rgba(21, 91, 127, 0.5), rgba(27, 219, 134, 0.5)) border-box;
}

.ideal-bar {
  flex: none;
  width: 4px;
  height: 28px;
  border-radius: 2px;
  background: #84ffc1;
}

.ideal em {
  font-style: normal;
  color: #d7dcdc;
  font-size: 16px;
  line-height: 22px;
}

.ideal strong {
  font-size: 16px;
  line-height: 22px;
}

@media (max-width: 1199px) {
  .v-d,
  .v-dm,
  .list-dm {
    display: none;
  }

  .v-t {
    display: inline;
  }

  .list-t {
    display: flex;
  }

  .summit {
    margin-top: 48px;
  }

  .panel {
    width: calc(100% - 72px);
    height: auto;
    margin: 0 auto;
    padding: 24px 16px 16px;
    border-radius: 20px;
  }

  .tabs {
    justify-content: flex-start;
    overflow-x: auto;
    scrollbar-width: none;
    padding-bottom: 4px;
  }

  .tabs::-webkit-scrollbar {
    display: none;
  }

  .tab {
    flex: none;
    height: 42px;
    padding: 0 20px;
    font-size: 14px;
  }

  .tab:nth-child(n) {
    width: auto;
  }

  h2 {
    margin-top: 20px;
    font-size: 36px;
    line-height: 1.2;
  }

  .meta {
    margin-top: 22px;
    height: 44px;
  }

  .meta-item {
    font-size: 14px;
    gap: 8px;
    padding-left: 14px;
  }

  .body {
    flex-direction: column;
    height: auto;
    gap: 20px;
    margin-top: 22px;
    padding: 16px;
  }

  ul {
    margin-top: 16px;
    gap: 14px;
  }

  .ideal {
    height: auto;
    min-height: 78px;
    margin-top: 16px;
  }

  .photo-card {
    display: none;
  }

  .photo-plain {
    display: block;
    width: 100%;
    height: 298px;
  }

  .lead {
    font-size: 18px;
    line-height: 28px;
  }

  li {
    font-size: 15px;
    line-height: 23px;
  }

  li:nth-child(3) {
    margin-top: 0;
  }
}

@media (max-width: 599px) {
  .v-t,
  .v-dt,
  .list-t {
    display: none;
  }

  .v-m,
  .v-dm {
    display: inline;
  }

  .list-dm {
    display: flex;
  }

  .summit {
    margin-top: 36px;
  }

  .panel {
    padding: 0;
    width: 100%;
    border-radius: 0;
    background: transparent;
    box-shadow: none;
    -webkit-backdrop-filter: none;
    backdrop-filter: none;
  }

  .tabs {
    padding: 0 16px 4px;
    gap: 10px;
  }

  .tab {
    height: 38px;
    padding: 0 18px;
    font-size: 13px;
  }

  h2 {
    margin: 20px 16px 0;
    text-align: left;
    font-size: 28px;
  }

  .meta {
    margin: 18px 16px 0;
    height: 40px;
  }

  .meta-item {
    font-size: 11px;
    gap: 5px;
    padding-left: 8px;
  }

  .meta-item svg {
    width: 14px;
    height: 14px;
  }

  .body {
    margin: 18px 16px 0;
    padding: 0;
    border: 0;
    background: transparent;
    gap: 18px;
  }

  .photo-plain {
    height: 200px;
  }

  .lead {
    font-size: 16px;
    line-height: 25px;
  }

  li {
    font-size: 14px;
    line-height: 22px;
  }

  .ideal {
    margin-top: 20px;
  }

  .ideal em,
  .ideal strong {
    font-size: 15px;
  }
}
</style>
