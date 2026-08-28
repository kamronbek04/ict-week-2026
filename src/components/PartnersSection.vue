<script setup>
const logos = import.meta.glob('../assets/par-*.svg', { eager: true, import: 'default' })

const items = [
  { id: 'aws', name: 'AWS', size: 'sm', width: 124, height: 81 },
  { id: 'startupblink', name: 'StartupBlink', size: 'sm', width: 196, height: 34 },
  { id: 'swc', name: 'Startup World Cup', size: 'sm', width: 76, height: 93 },
  { id: 'difc', name: 'DIFC Innovation Hub', size: 'sm', width: 204, height: 66 },
  { id: 'pegasus', name: 'Pegasus Tech Ventures', size: 'lg', width: 304, height: 97 },
  { id: 'jetro', name: 'JETRO', size: 'lg', width: 224, height: 77 },
  { id: 'ignyte', name: 'Ignyte', size: 'lg', width: 304, height: 40 }
]

const src = (name) => logos[`../assets/par-${name}.svg`]
</script>

<template>
  <section id="partners" class="partners">
    <div class="panel">
      <h2>Our Partners</h2>
      <div class="grid">
        <div v-for="it in items" :key="it.id" class="partner-card bordered" :class="it.size">
          <img
            :src="src(it.id)"
            :alt="it.name"
            class="partner-logo"
            :width="it.width"
            :height="it.height"
            loading="lazy"
          />
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.partners {
  margin-top: 73px;
}

.panel {
  width: 1280px;
  margin-left: 80px;
  padding: 36px 56px 56px;
  border-radius: 24px;
  background: var(--glass-panel);
  box-shadow: var(--glass-shadow);
  -webkit-backdrop-filter: var(--glass-filter);
  backdrop-filter: var(--glass-filter);
}

h2 {
  color: #ededf2;
  text-align: center;
  font-size: 48px;
  line-height: 58px;
  font-weight: 600;
  letter-spacing: -1.44px;
}

.grid {
  display: grid;
  grid-template-columns: repeat(12, 1fr);
  gap: 32px;
  margin-top: 56px;
}

.partner-card {
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 140px;
  overflow: hidden;
  border-radius: 12px;
  background: rgba(0, 0, 0, 0.01);
  -webkit-backdrop-filter: blur(4px);
  backdrop-filter: blur(4px);
}

.partner-card.bordered {
  isolation: isolate;
}

.partner-card.bordered::before {
  position: absolute;
  z-index: -1;
  inset: 0;
  padding: 1px;
  border-radius: inherit;
  background: linear-gradient(90deg, rgba(21, 91, 127, 0.3), rgba(27, 219, 134, 0.3));
  content: '';
  pointer-events: none;
  -webkit-mask:
    linear-gradient(#000 0 0) content-box,
    linear-gradient(#000 0 0);
  mask:
    linear-gradient(#000 0 0) content-box,
    linear-gradient(#000 0 0);
  -webkit-mask-composite: xor;
  mask-composite: exclude;
}

.partner-card.sm {
  grid-column: span 3;
}

.partner-card.lg {
  grid-column: span 4;
}

.partner-logo {
  display: block;
  width: auto;
  height: auto;
  max-width: calc(100% - 32px);
  max-height: calc(100% - 24px);
}

@media (max-width: 1199px) {
  .partners {
    margin-top: 48px;
  }

  .panel {
    width: calc(100% - 72px);
    margin: 0 auto;
    padding: 30px 20px 20px;
    border-radius: 20px;
  }

  h2 {
    font-size: 34px;
    line-height: 41px;
    letter-spacing: -1.02px;
  }

  .grid {
    margin-top: 26px;
    gap: 14px;
  }

  .partner-card {
    height: 120px;
  }
}

@media (max-width: 599px) {
  .partners {
    margin-top: 36px;
  }

  .panel {
    width: calc(100% - 32px);
    padding: 24px 14px 20px;
    border-radius: 16px;
  }

  h2 {
    font-size: 28px;
    line-height: 34px;
    letter-spacing: -0.84px;
  }

  .grid {
    grid-template-columns: repeat(2, minmax(0, 1fr));
    gap: 10px;
    margin-top: 18px;
  }

  .partner-card.sm,
  .partner-card.lg {
    grid-column: span 1;
    height: 96px;
  }

  .partner-card:last-child {
    grid-column: 1 / -1;
    height: 110px;
  }

  .partner-logo {
    max-width: calc(100% - 24px);
    max-height: calc(100% - 20px);
  }
}
</style>
