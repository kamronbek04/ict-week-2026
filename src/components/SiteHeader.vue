<script setup>
import logo from '../assets/logo.png'

const links = [
  { label: 'Home', href: '#', active: true },
  { label: 'Program', href: '#program' },
  { label: 'Partners', href: '#partners' },
  { label: 'Incentives', href: '#incentives', wide: true },
  { label: 'Exhibition', href: '#incentives', narrow: true }
]
</script>

<template>
  <header class="header">
    <div class="bar">
      <a href="#" class="brand">
        <img :src="logo" alt="ICT Week 2026 Uzbekistan" width="104" height="56" />
      </a>
      <nav class="nav" aria-label="Main">
        <a
          v-for="l in links"
          :key="l.label"
          :href="l.href"
          class="nav-link"
          :class="{ active: l.active, wide: l.wide, narrow: l.narrow }"
        >{{ l.label }}</a>
      </nav>
      <div class="actions">
        <button type="button" class="lang">
          English
          <svg width="16" height="16" viewBox="0 0 16 16" fill="none" aria-hidden="true">
            <path d="M4 6l4 4 4-4" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round" />
          </svg>
        </button>
        <a href="#register" class="cta">Register now</a>
        <button type="button" class="burger" aria-label="Menu">
          <span></span><span></span><span></span>
        </button>
      </div>
    </div>
  </header>
</template>

<style scoped>
.header {
  position: absolute;
  top: 37px;
  left: 0;
  right: 0;
  z-index: 10;
}

.bar {
  width: 1040px;
  height: 80px;
  margin: 0 auto;
  display: flex;
  align-items: center;
  padding: 0 14px 0 22px;
  border: 1px solid rgba(255, 255, 255, 0.18);
  border-radius: 20px;
  background: rgba(9, 22, 20, 0.72);
  backdrop-filter: blur(12px);
}

.brand img {
  width: 86px;
  height: auto;
}

.nav {
  display: flex;
  align-items: center;
  gap: 8px;
  margin-left: 116px;
}

.nav-link {
  padding: 12px 14px;
  font-size: 16px;
  font-weight: 500;
  color: #e5e9e9;
  border-radius: 24px;
}

.nav-link.active {
  padding: 12px 33px;
  background: #102829;
  border: 1px solid rgba(255, 255, 255, 0.16);
  color: #fff;
}

.nav-link.narrow {
  display: none;
}

.actions {
  margin-left: auto;
  display: flex;
  align-items: center;
  gap: 13px;
}

.lang {
  display: flex;
  align-items: center;
  gap: 6px;
  height: 47px;
  padding: 0 16px;
  border: 1px solid rgba(255, 255, 255, 0.2);
  border-radius: 24px;
  color: #fff;
  font-size: 16px;
}

.cta {
  display: flex;
  align-items: center;
  height: 47px;
  padding: 0 24px;
  border-radius: 26px;
  background: #63ca96;
  color: #121b26;
  font-size: 16px;
  font-weight: 600;
}

.burger {
  display: none;
}

@media (max-width: 1199px) {
  .header {
    top: 32px;
  }

  .bar {
    width: calc(100% - 48px);
    height: 62px;
    padding: 0 10px 0 16px;
    border-radius: 16px;
  }

  .brand img {
    width: 64px;
  }

  .nav {
    margin-left: 40px;
    gap: 2px;
  }

  .nav-link {
    padding: 9px 10px;
    font-size: 14px;
  }

  .nav-link.active {
    padding: 9px 18px;
  }

  .nav-link.wide {
    display: none;
  }

  .nav-link.narrow {
    display: block;
  }

  .lang {
    height: 38px;
    padding: 0 12px;
    font-size: 14px;
  }

  .cta {
    height: 38px;
    padding: 0 18px;
    font-size: 14px;
  }

  .actions {
    gap: 10px;
  }
}

@media (max-width: 599px) {
  .header {
    top: 0;
  }

  .bar {
    width: 100%;
    height: 64px;
    padding: 0 16px;
    border: 0;
    border-radius: 0;
    background: rgba(2, 10, 10, 0.85);
  }

  .brand img {
    width: 62px;
  }

  .nav,
  .lang {
    display: none;
  }

  .cta {
    height: 36px;
    padding: 0 20px;
    border-radius: 20px;
  }

  .burger {
    display: flex;
    flex-direction: column;
    justify-content: center;
    gap: 5px;
    width: 36px;
    height: 36px;
    padding: 8px;
    border-radius: 8px;
    background: rgba(255, 255, 255, 0.08);
  }

  .burger span {
    height: 2px;
    border-radius: 1px;
    background: #fff;
  }
}
</style>
