<script setup>
import panel from '../assets/hero-panel.webp'
import poster from '../assets/hero-poster.webp'
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
        <img :src="poster" alt="Aerial view of the ICT Week venue in Tashkent" width="769" height="488" fetchpriority="high" />
        <button type="button" class="play" aria-label="Play ICT Week video">
          <span class="play-inner" aria-hidden="true">
            <span class="play-core">
              <svg width="13" height="14" viewBox="384.5 242.4 13 14" fill="none">
                <path d="M385.149 249.362V244.467C385.149 242.98 386.758 242.049 388.048 242.791L392.313 245.243L396.56 247.685C397.853 248.429 397.853 250.295 396.56 251.039L392.313 253.481L388.048 255.933C386.758 256.675 385.149 255.744 385.149 254.257V249.362Z" fill="#121B26" />
              </svg>
            </span>
          </span>
        </button>
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
  font-size: 72px;
  line-height: 84px;
  font-weight: 600;
  letter-spacing: -2.16px;
}

.subtitle {
  display: none;
}

.grid {
  width: 1280px;
  margin: 48px 0 0 80px;
  display: grid;
  grid-template-columns: 781px 483px;
  gap: 16px;
}

.video {
  position: relative;
  width: 781px;
  height: 500px;
  padding: 6px;
  border-radius: 24px;
  overflow: hidden;
  background:
    radial-gradient(ellipse 194px 124px at 49% 1%, rgba(255, 255, 255, 0.95), rgba(255, 255, 255, 0.1)),
    radial-gradient(ellipse 302px 153px at 50% 0%, rgba(132, 255, 193, 0.7), rgba(132, 255, 193, 0));
  -webkit-backdrop-filter: blur(24.982px);
  backdrop-filter: blur(24.982px);
}

.video img {
  width: 769px;
  height: 488px;
  border-radius: 17.1919px;
  object-fit: cover;
}

.play {
  position: absolute;
  top: 215.664px;
  left: 356.386px;
  display: flex;
  align-items: center;
  justify-content: center;
  width: 68.7677px;
  height: 68.7677px;
  border-radius: 50%;
}

.play-inner {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 54.4411px;
  height: 54.4411px;
  border: 0.644697px solid rgba(255, 255, 255, 0.1);
  border-radius: 50%;
  background: linear-gradient(180deg, rgba(0, 0, 0, 0.2), rgba(0, 0, 0, 0));
  -webkit-backdrop-filter: blur(3.87px);
  backdrop-filter: blur(3.87px);
}

.play-core {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 37.2495px;
  height: 37.2495px;
  border-radius: 50%;
  background: linear-gradient(180deg, #84ffc1 0%, #459b6f 100%);
}

.play svg {
  display: block;
}

.play:hover .play-core,
.play:focus-visible .play-core {
  filter: brightness(1.08);
}

.play:focus-visible {
  outline: 2px solid #84ffc1;
  outline-offset: 3px;
}

.panel {
  width: 483px;
  height: 500px;
  border-radius: 24px;
  background: rgba(18, 27, 38, 0.3);
  box-shadow: var(--glass-shadow);
  -webkit-backdrop-filter: var(--glass-filter);
  backdrop-filter: var(--glass-filter);
  padding: 24px;
}

.panel-img {
  width: 435px;
  height: 187px;
  border-radius: 16px;
  object-fit: cover;
}

.panel-photo {
  display: none;
  border-radius: 12px;
  object-fit: cover;
}

.panel-text {
  margin-top: 16px;
  font-size: 18px;
  line-height: 24px;
  font-weight: 500;
}

.panel-actions {
  display: flex;
  gap: 16px;
  margin-top: 20px;
}

.btn-solid {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  gap: 8px;
  width: 178px;
  height: 52px;
  padding: 0;
  border-radius: 12px;
  background: #84ffc1;
  color: #121b26;
  font-size: 16px;
  font-weight: 600;
}

.btn-line {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  gap: 8px;
  width: 167px;
  height: 52px;
  padding: 0;
  border-radius: 12px;
  border: 1px solid #84ffc1;
  color: #84ffc1;
  font-size: 16px;
  font-weight: 600;
}

.count {
  display: flex;
  gap: 16px;
  margin-top: 32px;
}

.count-card {
  width: 134.333px;
  height: 97px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  border-radius: 16px;
  border: 1px solid var(--glass-line);
  background: rgba(18, 27, 38, 0.5);
  box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.04);
  -webkit-backdrop-filter: blur(6px);
  backdrop-filter: blur(6px);
}

.count-num {
  font-size: 36px;
  line-height: 43px;
  font-weight: 600;
}

.count-label {
  font-size: 18px;
  line-height: 22px;
  font-weight: 400;
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
    width: 100%;
    height: auto;
    padding-top: 5px;
    padding-right: 5px;
    padding-bottom: 5px;
    padding-left: 5px;
  }

  .video img {
    width: 100%;
    height: 335px;
  }

  .play {
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
  }

  .panel {
    width: 100%;
    height: auto;
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
    width: auto;
    height: 46px;
    padding: 0 20px;
    font-size: 15px;
  }

  .count {
    margin-top: 18px;
    gap: 16px;
  }

  .count-card {
    width: auto;
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
    line-height: normal;
  }
}
</style>
