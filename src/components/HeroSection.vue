<script setup>
import panel from '../assets/hero-panel.webp'

const posterUrl = import.meta.env.BASE_URL + 'hero-poster.webp'
import scaling from '../assets/hero-scaling.webp'

const countdown = [
  { value: '81', label: 'Days' },
  { value: '21', label: 'Hours' },
  { value: '15', label: 'Minutes' }
]
</script>

<template>
  <section class="hero">
    <h1 class="title">
      <span class="t-wide">Unlock the World&rsquo;s Fastest<br />Growing Ecosystem</span>
      <span class="t-narrow">Unlock the World&rsquo;s<br />Fastest Growing<br />Ecosystem</span>
    </h1>
    <p class="subtitle">
      Learn everything about the thriving Uzbek tech ecosystem &mdash; in just one
      week. Meet 10k+ attendees, global VCs &amp; partners.
    </p>
    <div class="grid">
      <div class="video">
        <img :src="posterUrl" alt="Aerial view of the ICT Week venue in Tashkent" width="771" height="491" fetchpriority="high" />
      </div>
      <aside class="panel">
        <img class="panel-img" :src="panel" alt="ICT Week talent availability dashboard" width="434" height="188" loading="lazy" />
        <div class="panel-main">
          <div class="panel-copy">
            <p class="panel-text">
              <span class="t-wide">learn everything about the thriving uzbek tech ecosystem &mdash; in just one week</span>
              <span class="t-narrow">Learn everything about the thriving Uzbek tech ecosystem &mdash; in just one week</span>
            </p>
            <div class="panel-actions">
              <a href="#register" class="btn-solid">
                Register now
                <svg width="16" height="16" viewBox="0 0 16 16" fill="none" aria-hidden="true">
                  <path d="M4.5 11.5l7-7M6 4.5h5.5V10" stroke="currentColor" stroke-width="1.6" stroke-linecap="round" stroke-linejoin="round" />
                </svg>
              </a>
              <a href="#program" class="btn-line">
                <svg width="17" height="16" viewBox="0 0 17 16" fill="none" aria-hidden="true">
                  <path d="M8.5 2v8m0 0l3-3m-3 3l-3-3M3 13h11" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round" />
                </svg>
                Full agenda
              </a>
            </div>
          </div>
          <img class="panel-photo" :src="scaling" alt="Scaling startups across borders panel at ICT Week" width="324" height="228" loading="lazy" />
        </div>
        <div class="count">
          <div v-for="c in countdown" :key="c.label" class="count-card">
            <span class="count-num">{{ c.value }}</span>
            <span class="count-label">{{ c.label }}</span>
          </div>
        </div>
      </aside>
    </div>
  </section>
</template>

<style scoped>
.t-narrow {
  display: none;
}

.hero {
  padding-top: 184px;
}

.title {
  text-align: center;
  font-size: 64px;
  line-height: 80px;
  font-weight: 600;
  letter-spacing: -1.5px;
}

.subtitle {
  display: none;
}

.grid {
  width: 1275px;
  margin: 64px 0 0 85px;
  display: grid;
  grid-template-columns: 772px 480px;
  justify-content: space-between;
}

.video {
  position: relative;
  padding-top: 6px;
  border-radius: 24px;
  overflow: hidden;
  background: #020205;
}

.video::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 6px;
  background: linear-gradient(90deg, rgba(129, 199, 175, 0) 0%, #81c7af 30%, #f2ffff 50%, #81c7af 70%, rgba(129, 199, 175, 0) 100%);
}

.video img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.panel {
  border: 1px solid rgba(255, 255, 255, 0.18);
  border-radius: 24px;
  background: #050c11;
  padding: 23px 23px 19px;
}

.panel-img {
  border-radius: 12px;
  border: 1px solid rgba(255, 255, 255, 0.12);
}

.panel-photo {
  display: none;
  border-radius: 12px;
  object-fit: cover;
}

.panel-text {
  margin-top: 19px;
  font-size: 20px;
  line-height: 26px;
  font-weight: 500;
}

.panel-actions {
  display: flex;
  gap: 16px;
  margin-top: 15px;
}

.btn-solid {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  height: 52px;
  padding: 0 24px;
  border-radius: 12px;
  background: #84ffc1;
  color: #121b26;
  font-size: 16px;
  font-weight: 600;
}

.btn-line {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  height: 52px;
  padding: 0 24px;
  border-radius: 12px;
  border: 1px solid #84ffc1;
  color: #84ffc1;
  font-size: 16px;
  font-weight: 600;
}

.count {
  display: flex;
  justify-content: space-between;
  margin-top: 27px;
}

.count-card {
  width: 133px;
  height: 97px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 2px;
  border-radius: 12px;
  border: 1px solid rgba(255, 255, 255, 0.14);
  background: #0a121a;
}

.count-num {
  font-size: 32px;
  line-height: 1.1;
  font-weight: 700;
}

.count-label {
  font-size: 13px;
  font-weight: 600;
  letter-spacing: 0.06em;
  text-transform: uppercase;
  color: #84ffc1;
}

@media (max-width: 1199px) {
  .hero {
    padding-top: 144px;
  }

  .title {
    font-size: 40px;
    line-height: 50px;
    letter-spacing: -0.5px;
  }

  .grid {
    width: calc(100% - 72px);
    margin: 48px auto 0;
    display: block;
  }

  .video {
    padding-top: 5px;
  }

  .video img {
    height: 335px;
  }

  .panel {
    margin-top: 32px;
    padding: 20px 20px 12px;
  }

  .panel-img {
    display: none;
  }

  .panel-main {
    display: flex;
    justify-content: space-between;
    gap: 22px;
  }

  .panel-photo {
    display: block;
    flex: none;
    width: 284px;
    height: 136px;
  }

  .panel-text {
    margin-top: 0;
    font-size: 20px;
    line-height: 28px;
  }

  .panel-actions {
    margin-top: 12px;
  }

  .btn-solid,
  .btn-line {
    height: 46px;
    padding: 0 20px;
    font-size: 15px;
  }

  .count {
    margin-top: 18px;
    gap: 16px;
  }

  .count-card {
    flex: 1;
    height: 86px;
  }
}

@media (max-width: 599px) {
  .t-wide {
    display: none;
  }

  .t-narrow {
    display: inline;
  }

  .hero {
    padding-top: 108px;
  }

  .title {
    font-size: 32px;
    line-height: 40px;
  }

  .subtitle {
    display: block;
    width: calc(100% - 48px);
    margin: 10px auto 0;
    text-align: center;
    font-size: 14px;
    line-height: 21px;
    color: #b7c0bf;
  }

  .grid {
    width: calc(100% - 32px);
    margin-top: 22px;
  }

  .video {
    border-radius: 16px;
  }

  .video img {
    height: 196px;
  }

  .panel {
    margin-top: 22px;
    padding: 16px 16px 16px;
    border-radius: 16px;
  }

  .panel-main {
    flex-direction: column-reverse;
    gap: 12px;
  }

  .panel-photo {
    width: 100%;
    height: 228px;
  }

  .panel-text {
    font-size: 18px;
    line-height: 25px;
  }

  .panel-actions {
    margin-top: 14px;
    gap: 12px;
  }

  .btn-solid {
    flex: 1;
    justify-content: center;
  }

  .btn-line {
    flex: 1;
    justify-content: center;
  }

  .count {
    margin-top: 16px;
    gap: 10px;
  }

  .count-card {
    height: 64px;
    gap: 0;
  }

  .count-num {
    font-size: 22px;
  }

  .count-label {
    font-size: 10.5px;
  }
}
</style>
