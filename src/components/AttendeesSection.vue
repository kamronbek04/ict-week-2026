<script setup>
const svgLogos = import.meta.glob('../assets/att-*.svg', { eager: true, import: 'default' })

const main = [
  'websummit', 'plugandplay', 'mit', 'google-startups', 'aws',
  'alchemist', 'dealroom', 'startupblink', 'domino', 'startup-genome',
  'accesa', 'sturgeon', 'salesforce', 'ey', 'gsa'
]
const wide = ['gbtp', 'polyvalent', 'goldengate', 'sps']

const names = {
  websummit: 'Web Summit',
  plugandplay: 'Plug and Play',
  mit: 'Massachusetts Institute of Technology',
  'google-startups': 'Google for Startups',
  aws: 'AWS',
  alchemist: 'Alchemist Accelerator',
  dealroom: 'Dealroom.co',
  startupblink: 'StartupBlink',
  domino: 'Domino Ventures',
  'startup-genome': 'Startup Genome',
  accesa: 'Accesa',
  sturgeon: 'Sturgeon Capital',
  salesforce: 'Salesforce.org',
  ey: 'EY',
  gsa: 'Global Startup Awards',
  gbtp: 'GBTP Gyeongbuk Technopark',
  polyvalent: 'Polyvalent',
  goldengate: 'Golden Gate Ventures',
  sps: 'SPS Commerce'
}

const dimensions = {
  accesa: { width: 144, height: 49 },
  alchemist: { width: 168, height: 29 },
  aws: { width: 96, height: 62 },
  dealroom: { width: 152, height: 37 },
  domino: { width: 144, height: 39 },
  ey: { width: 80, height: 80 },
  gbtp: { width: 188, height: 58 },
  goldengate: { width: 188, height: 74 },
  'google-startups': { width: 136, height: 20 },
  gsa: { width: 124, height: 64 },
  mit: { width: 152, height: 36 },
  plugandplay: { width: 144, height: 28 },
  polyvalent: { width: 196, height: 22 },
  salesforce: { width: 144, height: 67 },
  sps: { width: 196, height: 54 },
  'startup-genome': { width: 152, height: 41 },
  startupblink: { width: 160, height: 27 },
  sturgeon: { width: 144, height: 52 },
  websummit: { width: 136, height: 68 }
}

const getSvg = (id) => svgLogos[`../assets/att-${id}.svg`]
</script>

<template>
  <section class="attendees">
    <div class="panel">
      <h2>Past Attendees Include</h2>
      <div class="grid main">
        <div v-for="id in main" :key="id" class="card" :class="id">
          <img
            :src="getSvg(id)"
            :alt="names[id]"
            :width="dimensions[id]?.width"
            :height="dimensions[id]?.height"
            loading="lazy"
          />
        </div>
      </div>
      <div class="grid wide">
        <div v-for="id in wide" :key="id" class="card wide" :class="id">
          <img
            :src="getSvg(id)"
            :alt="names[id]"
            :width="dimensions[id]?.width"
            :height="dimensions[id]?.height"
            loading="lazy"
          />
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.attendees {
  margin-top: 68px;
}

.panel {
  max-width: 1280px;
  width: 100%;
  margin: 0 auto;
  padding: 48px 56px 56px;
  border-radius: 24px;
  background: var(--glass-panel);
  box-shadow: var(--glass-shadow);
  -webkit-backdrop-filter: var(--glass-filter);
  backdrop-filter: var(--glass-filter);
  box-sizing: border-box;
}

h2 {
  text-align: center;
  font-size: 40px;
  font-weight: 600;
  color: #ededf2;
  letter-spacing: -0.5px;
  margin: 0 0 48px;
}

.grid {
  display: grid;
  gap: 32px;
  justify-content: center;
}

.grid.main {
  grid-template-columns: repeat(5, 208px);
}

.grid.wide {
  grid-template-columns: repeat(4, 268px);
  margin-top: 32px;
}

.card {
  width: 208px;
  height: 120px;
  border-radius: 12px;
  background: var(--glass-card);
  border: 1px solid var(--glass-line);
  box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.035);
  -webkit-backdrop-filter: blur(6px);
  backdrop-filter: blur(6px);
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 16px 22px;
  box-sizing: border-box;
  transition: transform 0.25s ease, border-color 0.25s ease, background-color 0.25s ease, box-shadow 0.25s ease;
}

.card.wide {
  width: 268px;
}

.card:hover {
  transform: translateY(-3px);
  border-color: rgba(27, 219, 134, 0.4);
  background: rgba(27, 219, 134, 0.03);
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.35);
}

.card img {
  max-width: 100%;
  max-height: 100%;
  width: auto;
  height: auto;
  object-fit: contain;
  transition: transform 0.25s ease;
}

.card:hover img {
  transform: scale(1.03);
}

@media (max-width: 1279px) {
  .attendees {
    margin-top: 48px;
  }

  .panel {
    width: calc(100% - 48px);
    margin: 0 auto;
    padding: 36px 24px;
    border-radius: 20px;
  }

  h2 {
    font-size: 34px;
    margin-bottom: 32px;
  }

  .grid {
    gap: 16px;
  }

  .grid.main {
    grid-template-columns: repeat(5, 1fr);
  }

  .grid.wide {
    grid-template-columns: repeat(4, 1fr);
    margin-top: 16px;
  }

  .card,
  .card.wide {
    width: auto;
    height: 100px;
    padding: 12px 14px;
  }
}

@media (max-width: 899px) {
  .attendees {
    margin-top: 36px;
  }

  .panel {
    width: calc(100% - 32px);
    padding: 28px 16px;
    border-radius: 18px;
  }

  h2 {
    font-size: 28px;
    margin-bottom: 24px;
  }

  .grid {
    gap: 12px;
  }

  .grid.main {
    grid-template-columns: repeat(3, 1fr);
  }

  .grid.wide {
    grid-template-columns: repeat(2, 1fr);
    margin-top: 12px;
  }

  .card,
  .card.wide {
    height: 90px;
    padding: 10px 12px;
  }
}

@media (max-width: 599px) {
  .attendees {
    margin-top: 28px;
  }

  .panel {
    width: calc(100% - 24px);
    padding: 24px 12px;
    border-radius: 16px;
  }

  h2 {
    font-size: 22px;
    margin-bottom: 18px;
  }

  .grid {
    gap: 8px;
  }

  .grid.main {
    grid-template-columns: repeat(2, 1fr);
  }

  .grid.wide {
    grid-template-columns: repeat(2, 1fr);
    margin-top: 8px;
  }

  .card,
  .card.wide {
    height: 76px;
    padding: 8px 10px;
  }
}
</style>
