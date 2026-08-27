<script setup>
import ministry from '../assets/logo-ministry.png'
import itpark from '../assets/logo-itpark.png'
import qrCard from '../assets/qr-card.png'

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
            <img :src="ministry" alt="Ministry of Digital Technologies of the Republic of Uzbekistan" width="145" height="42" loading="lazy" />
            <img :src="itpark" alt="IT Park Uzbekistan" width="96" height="46" loading="lazy" />
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
            Digital Startups Program &ndash; a <strong>$50 million</strong> initiative, launched for promising Uzbek tech startups.
            Funding, mentorship, intellectual property protection and access to the global market &ndash; all
            available on one platform &ndash; <strong>startupbase.uz</strong>
          </p>
          <a class="qr" href="https://startupbase.uz" target="_blank" rel="noopener">
            <img :src="qrCard" alt="Startup Base — scan to open startupbase.uz" width="280" height="114" loading="lazy" />
          </a>
        </div>
      </div>
      <div class="pager">
        <button type="button" class="arrow" aria-label="Previous program">
          <svg width="18" height="18" viewBox="0 0 18 18" fill="none" aria-hidden="true">
            <path d="M11 4l-5 5 5 5" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round" />
          </svg>
        </button>
        <span class="pager-label">DIGITAL STARTUPS PROGRAM</span>
        <button type="button" class="arrow next" aria-label="Next program">
          <svg width="18" height="18" viewBox="0 0 18 18" fill="none" aria-hidden="true">
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
  width: 1275px;
  margin-left: 85px;
  padding: 36px 0 66px;
  border-radius: 28px;
  background: #0c2627;
}

.board {
  width: 1204px;
  margin: 0 auto;
  border-radius: 16px;
  overflow: hidden;
  background: linear-gradient(180deg, #0d1a24 0%, #0a141d 100%);
}

.band {
  position: relative;
  display: flex;
  align-items: center;
  height: 58px;
  padding: 0 20px 0 26px;
  background: linear-gradient(90deg, #a4f4c5 0%, #7ed3a4 30%, #29564f 62%, rgba(12, 26, 32, 0.95) 88%);
}

.band-bar {
  width: 4px;
  height: 26px;
  border-radius: 2px;
  background: #0b1a14;
}

.band h2 {
  margin-left: 14px;
  font-size: 24px;
  letter-spacing: 0.04em;
  font-weight: 700;
  color: #0b1a14;
}

.band-logos {
  display: flex;
  align-items: center;
  gap: 20px;
  margin-left: auto;
}

.grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  column-gap: 18px;
  row-gap: 13px;
  padding: 24px 26px 0;
}

.row {
  display: flex;
  align-items: center;
  gap: 22px;
  min-height: 74px;
  padding: 12px 18px;
  border: 1px solid rgba(255, 255, 255, 0.05);
  border-radius: 12px;
  background: #111e28;
}

.num {
  flex: none;
  width: 90px;
  font-size: 26px;
  font-weight: 700;
  color: #84ffc1;
}

.num.icon {
  display: flex;
  align-items: center;
}

.text {
  font-size: 15px;
  line-height: 22px;
  color: #e2e7e7;
}

.footer {
  display: flex;
  gap: 15px;
  padding: 22px 26px 26px;
}

.pitch {
  flex: 1;
  padding: 18px 22px;
  border-radius: 12px;
  background: linear-gradient(90deg, #a8dfc0 0%, #79b59d 45%, rgba(47, 90, 86, 0.9) 100%);
  color: #0d1b19;
  font-size: 16px;
  line-height: 27px;
}

.qr {
  flex: none;
}

.qr img {
  border-radius: 12px;
}

.pager {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 48px;
  margin-top: 40px;
}

.arrow {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 74px;
  height: 74px;
  border-radius: 50%;
  border: 1px solid rgba(255, 255, 255, 0.14);
  background: #0a141a;
  color: #fff;
}

.arrow.next {
  background: #84ffc1;
  border-color: #84ffc1;
  color: #0b1a14;
}

.pager-label {
  font-size: 22px;
  font-weight: 700;
  letter-spacing: 0.04em;
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
    height: 34px;
    width: auto;
  }

  .grid {
    gap: 12px;
    padding: 16px 16px 0;
  }

  .row {
    gap: 14px;
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
    padding: 14px 16px;
    font-size: 14px;
    line-height: 22px;
  }

  .qr img {
    width: 236px;
    height: auto;
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
    font-size: 15px;
    line-height: 1.2;
    max-width: 150px;
    text-align: left;
  }

  .band-logos img {
    height: 28px;
  }

  .grid {
    grid-template-columns: 1fr;
    gap: 10px;
    padding: 14px 14px 0;
  }

  .row {
    min-height: 60px;
    padding: 8px 10px;
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
    font-size: 13.5px;
    line-height: 21px;
  }

  .qr img {
    width: 100%;
    max-width: 280px;
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
