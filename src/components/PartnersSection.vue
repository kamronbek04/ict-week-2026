<script setup>
const cards = import.meta.glob('../assets/par-*.png', { eager: true, import: 'default' })

const items = [
  { id: 'aws', name: 'AWS', size: 'sm' },
  { id: 'startupblink', name: 'StartupBlink', size: 'sm' },
  { id: 'swc', name: 'Startup World Cup', size: 'sm' },
  { id: 'difc', name: 'DIFC Innovation Hub', size: 'sm' },
  { id: 'pegasus', name: 'Pegasus Tech Ventures', size: 'lg' },
  { id: 'jetro', name: 'JETRO', size: 'lg' },
  { id: 'ignyte', name: 'Ignyte', size: 'lg' }
]

const src = (n) => cards[`../assets/par-${n}.png`]
const tsrc = (n) => cards[`../assets/par-t-${n}.png`]
</script>

<template>
  <section id="partners" class="partners">
    <div class="panel">
      <h2>Our Partners</h2>
      <div class="grid">
        <picture v-for="it in items" :key="it.id">
          <source media="(min-width: 600px) and (max-width: 1199px)" :srcset="tsrc(it.id)" />
          <img
            :src="src(it.id)"
            :alt="it.name"
            :class="it.size"
            :width="it.size === 'sm' ? 268 : 368"
            height="140"
            loading="lazy"
          />
        </picture>
      </div>
    </div>
  </section>
</template>

<style scoped>
.partners {
  margin-top: 73px;
}

.panel {
  width: 1275px;
  margin-left: 85px;
  padding: 34px 0 30px;
  border-radius: 28px;
  background: #071316;
}

h2 {
  text-align: center;
  font-size: 44px;
  font-weight: 600;
  letter-spacing: -0.5px;
}

.grid {
  display: grid;
  grid-template-columns: repeat(12, 1fr);
  gap: 32px;
  width: 1168px;
  margin: 56px 0 0 51px;
}

.grid picture {
  display: contents;
}

.grid source {
  display: none;
}

.grid img {
  width: 100%;
  height: auto;
  border-radius: 14px;
}

.grid img.sm {
  grid-column: span 3;
}

.grid img.lg {
  grid-column: span 4;
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
  }

  .grid {
    width: 100%;
    margin: 26px 0 0;
    gap: 14px;
  }

  .grid img {
    object-fit: cover;
  }

  .grid img.sm {
    aspect-ratio: 144 / 120;
  }

  .grid img.lg {
    aspect-ratio: 196 / 120;
  }
}

@media (max-width: 599px) {
  .partners {
    margin-top: 36px;
  }

  .grid img.sm,
  .grid img.lg {
    aspect-ratio: 268 / 140;
  }

  .panel {
    width: calc(100% - 32px);
    padding: 24px 14px 20px;
    border-radius: 16px;
  }

  h2 {
    font-size: 24px;
  }

  .grid {
    grid-template-columns: repeat(6, 1fr);
    gap: 10px;
    margin-top: 18px;
  }

  .grid img.sm {
    grid-column: span 2;
  }

  .grid picture:nth-child(4) img,
  .grid picture:nth-child(5) img,
  .grid img.lg {
    grid-column: span 3;
  }
}
</style>
