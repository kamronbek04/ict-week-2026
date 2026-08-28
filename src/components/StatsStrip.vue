<script setup>
import medal from '../assets/medal.webp'
import dealroom from '../assets/logo-dealroom.svg'
import startupblink from '../assets/logo-startupblink.svg'
import uzum from '../assets/logo-uzum.svg'
import tbc from '../assets/logo-tbc.svg'
import uniIcon from '../assets/uni-icon.svg'
</script>

<template>
  <section class="stats">
    <div class="inner">
      <img class="medal" :src="medal" alt="StartupBlink's Country of the Year award" width="150" height="150" loading="lazy" />
      <article class="card">
        <span class="tag">2026</span>
        <div class="col">
          <strong>$4.3B</strong>
          <span>Startup Ecosystem Valuation</span>
        </div>
        <div class="col">
          <strong>#1</strong>
          <span>In venture investment growth&ensp;globally</span>
        </div>
        <img class="brand" :src="dealroom" alt="Dealroom.co" width="92" height="22" loading="lazy" />
      </article>
      <article class="card">
        <span class="tag">2026</span>
        <img class="medal-m" :src="medal" alt="medal of honor" width="48" height="48" loading="lazy" />
        <div class="col">
          <strong>#1</strong>
          <span>Ecosystem in the World by Growth Rate</span>
        </div>
        <div class="col">
          <strong>#1</strong>
          <span>Startup Hub in Central Asia (Tashkent)</span>
        </div>
        <img class="brand" :src="startupblink" alt="StartupBlink" width="95" height="16" loading="lazy" />
      </article>
      <article class="card narrow">
        <span class="tag">2026</span>
        <div class="col">
          <div class="uni-header">
            <strong>2</strong>
            <img class="uni-icon" :src="uniIcon" alt="Fintech Unicorns" width="24" height="24" loading="lazy" />
          </div>
          <span>Fintech Unicorns</span>
        </div>
        <div class="banks">
          <img :src="uzum" alt="Uzum" width="90" height="24" loading="lazy" />
          <img :src="tbc" alt="TBC Bank" width="97" height="24" loading="lazy" />
        </div>
      </article>
    </div>
  </section>
</template>

<style scoped>
.stats {
  margin-top: 58px;
}

.inner {
  max-width: 1280px;
  width: 100%;
  margin: 0 auto;
  display: flex;
  align-items: center;
  height: 182px;
  padding: 0 28px 0 23px;
  border-radius: 24px;
  background: var(--glass-panel);
  box-shadow: var(--glass-shadow);
  -webkit-backdrop-filter: var(--glass-filter);
  backdrop-filter: var(--glass-filter);
}

.medal {
  flex: none;
  width: 150px;
  height: 150px;
  object-fit: contain;
  margin-right: 7px;
}

.card {
  position: relative;
  flex: none;
  display: flex;
  width: 371px;
  height: 108px;
  padding: 8px 14px 10px 20px;
  border-radius: 10.34px;
  background: rgba(3, 14, 18, 0.32);
  -webkit-backdrop-filter: blur(6px);
  backdrop-filter: blur(6px);
}

.card::before {
  content: '';
  position: absolute;
  inset: 0;
  border-radius: 10.34px;
  padding: 1.2px;
  background: linear-gradient(90deg, #155B7F 0%, #1BDB86 100%);
  -webkit-mask:
    linear-gradient(#fff 0 0) content-box,
    linear-gradient(#fff 0 0);
  -webkit-mask-composite: xor;
  mask-composite: exclude;
  pointer-events: none;
}

.card + .card {
  margin-left: 24px;
}

.card.narrow {
  width: 256px;
}

.tag {
  position: absolute;
  top: 0;
  right: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 25px;
  padding: 0 16px;
  background: #84ffc1;
  color: #121b26;
  font-size: 14px;
  font-weight: 700;
  border-radius: 0 9.14px 0 10px;
  letter-spacing: 0.02em;
}

.col {
  display: flex;
  flex-direction: column;
  width: 125px;
}

.col strong {
  font-size: 28px;
  line-height: 34px;
  font-weight: 700;
  color: #ffffff;
}

.uni-header {
  display: flex;
  align-items: center;
  gap: 8px;
}

.uni-icon {
  width: 24px;
  height: 24px;
  object-fit: contain;
}

.col span {
  margin-top: 4px;
  max-width: 96px;
  font-size: 12px;
  line-height: 15px;
  color: #ccd3d3;
}

.brand {
  position: absolute;
  right: 14px;
  bottom: 12px;
}

.banks {
  display: flex;
  flex-direction: column;
  gap: 10px;
  align-items: flex-end;
  margin: 20px 8px 0 auto;
}

.banks img:first-child {
  width: 72px;
  height: auto;
}

.banks img:last-child {
  width: 78px;
  height: auto;
}

.medal-m {
  display: none;
}

@media (max-width: 1299px) {
  .stats {
    margin-top: 68px;
  }

  .inner {
    width: calc(100% - 72px);
    margin: 0 auto;
    flex-wrap: wrap;
    align-items: center;
    height: auto;
    padding: 16px;
    gap: 12px;
  }

  .medal {
    width: 96px;
    height: 96px;
    margin-right: 0;
  }

  .card,
  .card + .card,
  .card.narrow {
    margin: 0;
    height: 110px;
  }

  .card:first-of-type {
    flex: 1;
    width: auto;
    margin-left: 12px;
  }

  .card:nth-of-type(2) {
    width: calc(54% - 7px);
  }

  .card.narrow {
    width: calc(46% - 7px);
  }
}

@media (max-width: 599px) {
  .stats {
    margin-top: 22px;
  }

  .inner {
    width: calc(100% - 32px);
    padding: 0;
    gap: 14px;
    background: none;
    border-radius: 0;
    box-shadow: none;
    -webkit-backdrop-filter: none;
    backdrop-filter: none;
  }

  .medal {
    display: none;
  }

  .medal-m {
    display: block;
    align-self: center;
    margin-right: 4px;
  }

  .card:first-of-type,
  .card:nth-of-type(2),
  .card.narrow {
    width: 100%;
    height: auto;
    margin: 0;
    padding: 12px 14px 14px 16px;
  }

  .card:first-of-type {
    min-height: 126px;
  }

  .card:nth-of-type(2) {
    min-height: 155px;
  }

  .card.narrow {
    min-height: 120px;
  }

  .col strong {
    font-size: 26px;
    line-height: 32px;
  }

  .col span {
    font-size: 12.5px;
    line-height: 16px;
  }

  .medal-m {
    width: 48px;
    height: auto;
  }

  .banks {
    margin: 26px 10px 0 auto;
    gap: 8px;
  }

  .banks img:first-child {
    width: 96px;
    height: auto;
  }

  .banks img:last-child {
    width: 100px;
    height: auto;
  }

  .card:nth-of-type(2) {
    align-items: center;
  }

  .col span {
    max-width: 110px;
  }
}
</style>
