<script setup>
import ministry from '../assets/logo-ministry.svg'
import itpark from '../assets/logo-itpark.svg'
import qrCode from '../assets/qr-card.svg'
import startupBase from '../assets/startup-base.svg'

const rows = [
  { num: '100%', text: 'Reimbursement for patenting and trademark registration' },
  { icon: true, text: 'Special legal regime "Regulatory Sandbox" for rapid piloting' },
  { num: '$50K', text: 'Reimbursement for mentor/trainer costs in acceleration programs' },
  { num: '1+1', text: 'Co-funding mechanism matching foreign investment dollar-for-dollar' },
  { num: '$20K', text: 'Reimbursement of international acceleration program costs' },
  { num: '1 YEAR', text: 'Free access to the massive Digital Data Platform for Startups' },
  { num: '1 YEAR', text: 'Free dedicated legal and financial consultations with top experts' },
  { num: '$10K', text: 'Awarding grants directly to winners of national hackathons and ideathons' }
]
</script>

<template>
  <section id="incentives" class="programs">
    <div class="panel">
      <div class="board">
        <header class="band">
          <span class="band-bar"></span>
          <h2>DIGITAL STARTUPS PROGRAM</h2>
          <div class="band-logos">
            <img :src="ministry" alt="Ministry of Digital Technologies of the Republic of Uzbekistan" width="123" height="32" loading="lazy" />
            <img :src="itpark" alt="IT Park Uzbekistan" width="92" height="30" loading="lazy" />
          </div>
        </header>
        <div class="grid">
          <div v-for="r in rows" :key="r.text" class="row">
            <span v-if="r.icon" class="num icon">
              <svg width="30" height="32" viewBox="0 0 30 32" fill="none" aria-hidden="true">
                <path d="M15 2l11 4v8c0 7-4.5 12.5-11 16C8.5 26.5 4 21 4 14V6l11-4z" stroke="#84ffc1" stroke-width="1.8" stroke-linejoin="round" />
                <path d="M10.5 15.5l3 3 6-6" stroke="#84ffc1" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round" />
              </svg>
            </span>
            <span v-else class="num">{{ r.num }}</span>
            <span class="text">{{ r.text }}</span>
          </div>
        </div>
        <div class="footer">
          <p class="pitch">
            Digital Startups Program a 50 million dollar initiative, launched for promising Uzbek tech startups.
            Funding, mentorship, intellectual property protection and access to the global market all available on one platform startupbase.uz
          </p>
          <a class="qr" href="https://startupbase.uz" target="_blank" rel="noopener" aria-label="Open Startup Base">
            <img class="startup-base-logo" :src="startupBase" alt="Startup Base" width="154" height="36" loading="lazy" />
            <img class="qr-code" :src="qrCode" alt="" width="88" height="88" loading="lazy" />
          </a>
        </div>
      </div>
      <div class="pager">
        <button type="button" class="arrow" aria-label="Previous program">
          <svg width="28" height="28" viewBox="0 0 18 18" fill="none" aria-hidden="true">
            <path d="M11 4l-5 5 5 5" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round" />
          </svg>
        </button>
        <span class="pager-label">DIGITAL STARTUPS PROGRAM</span>
        <button type="button" class="arrow next" aria-label="Next program">
          <svg width="28" height="28" viewBox="0 0 18 18" fill="none" aria-hidden="true">
            <path d="M7 4l5 5-5 5" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round" />
          </svg>
        </button>
      </div>
    </div>
  </section>
</template>

<style scoped>
.programs {
  margin-top: 68px;
}

.panel {
  width: 1280px;
  margin-left: 80px;
  padding: 36px;
  border-radius: 24px;
  background: var(--glass-panel);
  box-shadow: var(--glass-shadow);
  -webkit-backdrop-filter: var(--glass-filter);
  backdrop-filter: var(--glass-filter);
}

.board {
  position: relative;
  isolation: isolate;
  width: 100%;
  min-height: 624px;
  border-radius: 16px;
  overflow: hidden;
  background:
    linear-gradient(178deg, rgba(0, 0, 0, 0) 0%, rgba(32, 68, 118, 0.76) 100%),
    radial-gradient(ellipse 72% 100% at 50% 100%, #0c1e5b 0%, #010101 100%);
}

.board::before {
  position: absolute;
  z-index: 0;
  inset: 0;
  background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='176' height='136' viewBox='0 0 176 136'%3E%3Cg fill='%23fff' fill-opacity='.09'%3E%3Cpath d='M44 0 84 20.5v41L44 82 4 61.5v-41L44 0Z'/%3E%3Cpath d='m132 0 40 20.5v41L132 82 92 61.5v-41L132 0Z'/%3E%3Cpath d='m88 68 40 20.5v41L88 150l-40-20.5v-41L88 68Z'/%3E%3C/g%3E%3C/svg%3E");
  background-position: center bottom -6px;
  content: '';
  opacity: 0.36;
}

.board > * {
  position: relative;
  z-index: 1;
}

.band {
  position: relative;
  display: flex;
  align-items: center;
  height: 58px;
  padding: 0 24px;
  background: linear-gradient(90deg, #84ffc1 0%, #84ffc1 41%, rgba(132, 255, 193, 0) 100%);
}

.band-bar {
  flex: none;
  width: 2px;
  height: 22px;
  border-radius: 1px;
  background: #121b26;
}

.band h2 {
  margin-left: 14px;
  font-size: 24px;
  line-height: 1;
  letter-spacing: -0.025em;
  font-weight: 700;
  color: #121b26;
}

.band-logos {
  display: flex;
  align-items: center;
  gap: 16px;
  margin-left: auto;
}

.band-logos img {
  flex: none;
}

.grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 12px;
  padding: 28px 24px 0;
}

.row {
  display: flex;
  align-items: center;
  gap: 33px;
  height: 76px;
  padding: 12px 28px;
  border-radius: 16px;
  background: rgba(18, 27, 38, 0.52);
  box-shadow:
    inset 0 1px 0 rgba(255, 255, 255, 0.055),
    inset 0 0 0 1px var(--glass-line);
  -webkit-backdrop-filter: blur(6px);
  backdrop-filter: blur(6px);
}

.num {
  flex: none;
  width: 88px;
  font-size: 32px;
  line-height: 1;
  font-weight: 700;
  text-align: center;
  color: #84ffc1;
}

.num.icon {
  display: flex;
  align-items: center;
  justify-content: center;
}

.text {
  font-size: 16px;
  line-height: 24px;
  color: rgba(255, 255, 255, 0.82);
}

.footer {
  display: flex;
  gap: 12px;
  padding: 32px 24px 50px;
}

.pitch {
  flex: 1;
  display: flex;
  align-items: center;
  height: 116px;
  padding: 20px 26px;
  border-radius: 18px;
  background: linear-gradient(151deg, rgba(132, 255, 193, 0) 0%, rgba(132, 255, 193, 0.4) 100%);
  color: #fff;
  font-size: 18px;
  line-height: 24px;
}

.qr {
  flex: none;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 12px;
  width: 285px;
  height: 116px;
  padding: 14px;
  border-radius: 18px;
  background: linear-gradient(100deg, rgba(132, 255, 193, 0) 0%, rgba(132, 255, 193, 0.4) 100%);
  transition: border-color 0.2s ease, transform 0.2s ease;
}

.qr:hover,
.qr:focus-visible {
  box-shadow: inset 0 0 0 1px rgba(132, 255, 193, 0.55);
  transform: translateY(-2px);
}

.qr:focus-visible {
  outline: 2px solid #84ffc1;
  outline-offset: 3px;
}

.startup-base-logo,
.qr-code {
  flex: none;
}

.pager {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 24px;
  margin-top: 32px;
}

.arrow {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 72px;
  height: 72px;
  border-radius: 50%;
  border: 1px solid rgba(255, 255, 255, 0.14);
  background: rgba(18, 27, 38, 0.78);
  color: rgba(255, 255, 255, 0.52);
  transition: border-color 0.2s ease, transform 0.2s ease;
}

.arrow.next {
  background: rgba(132, 255, 193, 0.8);
  border-color: #84ffc1;
  color: #121b26;
}

.arrow:hover,
.arrow:focus-visible {
  border-color: #84ffc1;
  transform: translateY(-2px);
}

.arrow:focus-visible {
  outline: 2px solid #84ffc1;
  outline-offset: 3px;
}

.pager-label {
  font-size: 22px;
  line-height: 1;
  font-weight: 700;
  letter-spacing: -0.025em;
}

@media (max-width: 1199px) {
  .programs {
    margin-top: 44px;
  }

  .panel {
    width: calc(100% - 72px);
    margin: 0 auto;
    padding: 20px 0 30px;
    border-radius: 20px;
  }

  .board {
    width: calc(100% - 40px);
    min-height: 0;
    margin: 0 auto;
    border-radius: 12px;
  }

  .band {
    height: 52px;
    padding: 0 14px 0 18px;
  }

  .band h2 {
    font-size: 17px;
    margin-left: 10px;
  }

  .band-logos {
    gap: 12px;
  }

  .band-logos img {
    height: 26px;
    width: auto;
  }

  .grid {
    gap: 12px;
    padding: 16px 16px 0;
  }

  .row {
    gap: 14px;
    height: auto;
    min-height: 108px;
    padding: 12px 14px;
  }

  .num {
    width: 70px;
    font-size: 22px;
  }

  .num.icon svg {
    width: 24px;
    height: 26px;
  }

  .text {
    font-size: 14px;
    line-height: 20px;
  }

  .footer {
    gap: 12px;
    padding: 16px;
  }

  .pitch {
    height: auto;
    min-height: 104px;
    padding: 14px 16px;
    font-size: 14px;
    line-height: 22px;
  }

  .qr {
    width: 236px;
    height: auto;
    min-height: 104px;
    padding: 10px;
  }

  .startup-base-logo {
    width: 128px;
    height: auto;
  }

  .qr-code {
    width: 72px;
    height: 72px;
  }

  .pager {
    gap: 34px;
    margin-top: 26px;
  }

  .arrow {
    width: 56px;
    height: 56px;
  }

  .pager-label {
    font-size: 17px;
  }
}

@media (max-width: 599px) {
  .programs {
    margin-top: 36px;
  }

  .panel {
    width: calc(100% - 32px);
    padding: 14px 0 24px;
    border-radius: 16px;
  }

  .board {
    width: calc(100% - 28px);
  }

  .band {
    height: 64px;
    padding: 0 12px;
  }

  .band h2 {
    max-width: 120px;
    font-size: 13px;
    line-height: 1.2;
    text-align: left;
  }

  .band-logos img {
    height: 20px;
  }

  .band-logos {
    gap: 8px;
  }

  .grid {
    grid-template-columns: 1fr;
    gap: 10px;
    padding: 14px 14px 0;
  }

  .row {
    min-height: 76px;
    padding: 10px 12px;
  }

  .num {
    width: 62px;
    font-size: 18px;
  }

  .text {
    font-size: 12px;
    line-height: 17px;
  }

  .footer {
    flex-direction: column;
    padding: 14px;
  }

  .pitch {
    min-height: 0;
    font-size: 13.5px;
    line-height: 21px;
  }

  .qr {
    width: 100%;
    min-height: 100px;
    padding: 12px;
  }

  .startup-base-logo {
    width: 154px;
  }

  .qr-code {
    width: 76px;
    height: 76px;
  }

  .pager {
    gap: 20px;
    margin-top: 18px;
  }

  .arrow {
    width: 44px;
    height: 44px;
  }

  .pager-label {
    font-size: 13px;
  }
}
</style>
