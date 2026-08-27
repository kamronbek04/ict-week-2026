<script setup>
const cards = import.meta.glob('../assets/att-*.png', { eager: true, import: 'default' })

const main = [
  'websummit', 'plugandplay', 'mit', 'google-startups', 'aws',
  'alchemist', 'dealroom', 'startupblink', 'domino', 'startup-genome',
  'accesa', 'sturgeon', 'salesforce', 'ey', 'gsa'
]
const wide = ['gbtp', 'polyvalent', 'goldengate', 'sps']

const names = {
  websummit: 'Web Summit', plugandplay: 'Plug and Play', mit: 'Massachusetts Institute of Technology',
  'google-startups': 'Google for Startups', aws: 'AWS', alchemist: 'Alchemist Accelerator',
  dealroom: 'Dealroom.co', startupblink: 'StartupBlink', domino: 'Domino Ventures',
  'startup-genome': 'Startup Genome', accesa: 'Accesa', sturgeon: 'Sturgeon Capital',
  salesforce: 'Salesforce.org', ey: 'EY', gsa: 'Global Startup Awards', gbtp: 'GBTP Gyeongbuk Technopark',
  polyvalent: 'Polyvalent', goldengate: 'Golden Gate Ventures', sps: 'SPS Commerce'
}

const src = (n) => cards[`../assets/att-${n}.png`]
const tsrc = (n) => cards[`../assets/att-t-${n}.png`]
</script>

<template>
  <section class="attendees">
    <div class="panel">
      <h2>Past Attendees Include</h2>
      <div class="grid main">
        <picture v-for="n in main" :key="n">
          <source media="(min-width: 600px) and (max-width: 1199px)" :srcset="tsrc(n)" />
          <img :src="src(n)" :alt="names[n]" width="208" height="120" loading="lazy" />
        </picture>
      </div>
      <div class="grid wide">
        <picture v-for="n in wide" :key="n">
          <source media="(min-width: 600px) and (max-width: 1199px)" :srcset="tsrc(n)" />
          <img :src="src(n)" :alt="names[n]" width="268" height="120" loading="lazy" />
        </picture>
      </div>
    </div>
  </section>
</template>

<style scoped>
.attendees {
  margin-top: 68px;
}

.panel {
  width: 1275px;
  margin-left: 85px;
  padding: 30px 0 54px;
  border-radius: 28px;
  background: #0b1e21;
}

h2 {
  text-align: center;
  font-size: 44px;
  font-weight: 600;
  letter-spacing: -0.5px;
}

.grid {
  display: grid;
  gap: 32px;
  width: 1168px;
  margin: 32px 0 0 51px;
}

.grid picture {
  display: contents;
}

.grid source {
  display: none;
}

.grid.main {
  grid-template-columns: repeat(5, 1fr);
  margin-top: 60px;
}

.grid.wide {
  grid-template-columns: repeat(4, 1fr);
}

.grid img {
  width: 100%;
  height: auto;
  border-radius: 14px;
}

@media (max-width: 1199px) {
  .attendees {
    margin-top: 20px;
  }

  .panel {
    width: calc(100% - 72px);
    margin: 0 auto;
    padding: 30px 14px 20px;
    border-radius: 20px;
  }

  h2 {
    font-size: 34px;
  }

  .grid {
    width: 100%;
    margin: 12px 0 0;
    gap: 12px;
  }

  .grid img {
    object-fit: cover;
  }

  .grid.main img {
    aspect-ratio: 113 / 100;
  }

  .grid.wide img {
    aspect-ratio: 145 / 100;
  }

  .grid.main {
    margin-top: 21px;
  }
}

@media (max-width: 599px) {
  .attendees {
    margin-top: 36px;
  }

  .grid.main img {
    aspect-ratio: 208 / 120;
  }

  .grid.wide img {
    aspect-ratio: 268 / 120;
  }

  .panel {
    width: calc(100% - 32px);
    padding: 22px 12px 24px;
    border-radius: 16px;
  }

  h2 {
    font-size: 24px;
  }

  .grid {
    gap: 10px;
  }

  .grid.main {
    grid-template-columns: repeat(3, 1fr);
    margin-top: 22px;
  }

  .grid.wide {
    grid-template-columns: repeat(2, 1fr);
  }
}
</style>
