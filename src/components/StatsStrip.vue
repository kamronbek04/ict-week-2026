<script setup>
import medal from '../assets/medal.png'
import dealroom from '../assets/logo-dealroom.png'
import startupblink from '../assets/logo-startupblink.png'
import uzum from '../assets/logo-uzum.png'
import tbc from '../assets/logo-tbc.png'
import uniIcon from '../assets/uni-icon.png'
</script>

<template>
  <section class="stats">
    <div class="inner">
      <img class="medal" :src="medal" alt="StartupBlink's Country of the Year award" width="130" height="172" loading="lazy" />
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
        <img class="brand" :src="dealroom" alt="Dealroom.co" width="100" height="28" loading="lazy" />
      </article>
      <article class="card">
        <span class="tag">2026</span>
        <img class="medal-m" :src="medal" alt="" width="74" height="98" loading="lazy" />
        <div class="col">
          <strong>#1</strong>
          <span>Ecosystem in the World by Growth Rate</span>
        </div>
        <div class="col">
          <strong>#1</strong>
          <span>Startup Hub in Central Asia (Tashkent)</span>
        </div>
        <img class="brand" :src="startupblink" alt="StartupBlink" width="106" height="26" loading="lazy" />
      </article>
      <article class="card narrow">
        <span class="tag">2026</span>
        <div class="col">
          <img :src="uniIcon" alt="2" width="66" height="40" loading="lazy" />
          <span>Fintech Unicorns</span>
        </div>
        <div class="banks">
          <img :src="uzum" alt="Uzum" width="108" height="36" loading="lazy" />
          <img :src="tbc" alt="TBC Bank" width="114" height="34" loading="lazy" />
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
  width: 1275px;
  margin-left: 85px;
  display: flex;
  align-items: flex-start;
  height: 209px;
  padding: 18px 0 0 33px;
  border-radius: 24px;
  background: linear-gradient(90deg, #051d22 0%, #0b2b2f 100%);
}

.medal {
  flex: none;
}

.card {
  position: relative;
  flex: none;
  display: flex;
  width: 370px;
  height: 108px;
  margin: 22px 0 0 39px;
  padding: 8px 14px 10px 20px;
  border: 1px solid rgba(102, 255, 198, 0.32);
  border-radius: 12px;
  background: linear-gradient(180deg, #0a1520 0%, #071019 100%);
}

.card + .card {
  margin-left: 24px;
}

.card:nth-of-type(1) {
  background: #081118;
}

.card:nth-of-type(2) {
  background: #0a1b21;
}

.card:nth-of-type(3) {
  background: #0b2229;
}

.card.narrow {
  width: 259px;
}

.tag {
  position: absolute;
  top: 0;
  right: 0;
  display: flex;
  align-items: center;
  height: 24px;
  padding: 0 20px;
  background: #84ffc1;
  color: #0b1a14;
  font-size: 14px;
  font-weight: 700;
  border-radius: 0 11px 0 10px;
}

.col {
  display: flex;
  flex-direction: column;
  width: 125px;
}

.col strong {
  font-size: 30px;
  line-height: 38px;
  font-weight: 700;
}

.col img {
  margin-top: -2px;
}

.col span {
  margin-top: 3px;
  max-width: 96px;
  font-size: 13px;
  line-height: 17px;
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
  margin: 22px 14px 0 auto;
}

.medal-m {
  display: none;
}

@media (max-width: 1199px) {
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
    height: auto;
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
