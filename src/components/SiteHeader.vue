<script setup>
import { nextTick, onBeforeUnmount, onMounted, ref } from 'vue'
import logo from '../assets/logo.svg'

const links = [
  { label: 'Home', href: '#' },
  { label: 'Program', href: '#program' },
  { label: 'Partners', href: '#partners' },
  { label: 'Incentives', href: '#incentives' }
]

const nav = ref(null)
const activeHref = ref('#')
const mobileMenuOpen = ref(false)
let resizeFrame

const updateIndicator = () => {
  if (typeof window !== 'undefined' && window.innerWidth < 600) return
  const navElement = nav.value

  if (!navElement) return

  const activeLink = navElement.querySelector('.nav-link.is-active')
  if (!activeLink || activeLink.offsetParent === null) {
    navElement.classList.remove('has-indicator')
    return
  }

  // Batch DOM reads before DOM writes to eliminate forced reflow
  const x = activeLink.offsetLeft
  const y = activeLink.offsetTop
  const w = activeLink.offsetWidth
  const h = activeLink.offsetHeight

  // Batch DOM writes
  navElement.style.setProperty('--indicator-x', `${x}px`)
  navElement.style.setProperty('--indicator-y', `${y}px`)
  navElement.style.setProperty('--indicator-width', `${w}px`)
  navElement.style.setProperty('--indicator-height', `${h}px`)
  navElement.classList.add('has-indicator')
}

const scheduleIndicatorUpdate = () => {
  cancelAnimationFrame(resizeFrame)
  resizeFrame = requestAnimationFrame(updateIndicator)
}

const syncActiveLink = () => {
  const currentHash = window.location.hash || '#'
  activeHref.value = links.some((link) => link.href === currentHash) ? currentHash : '#'
  nextTick(scheduleIndicatorUpdate)
}

const activateLink = (href) => {
  activeHref.value = href
  nextTick(scheduleIndicatorUpdate)
}

const closeMobileMenu = () => {
  mobileMenuOpen.value = false
}

const toggleMobileMenu = () => {
  mobileMenuOpen.value = !mobileMenuOpen.value
}

const handleKeydown = (event) => {
  if (event.key === 'Escape') closeMobileMenu()
}

const handleResize = () => {
  if (window.innerWidth >= 600) closeMobileMenu()
  scheduleIndicatorUpdate()
}

onMounted(() => {
  syncActiveLink()
  window.addEventListener('hashchange', syncActiveLink)
  window.addEventListener('resize', handleResize)
  window.addEventListener('keydown', handleKeydown)
  document.fonts?.ready.then(scheduleIndicatorUpdate)
})

onBeforeUnmount(() => {
  cancelAnimationFrame(resizeFrame)
  window.removeEventListener('hashchange', syncActiveLink)
  window.removeEventListener('resize', handleResize)
  window.removeEventListener('keydown', handleKeydown)
})
</script>

<template>
  <header class="header">
    <div class="bar">
      <a href="#" class="brand">
        <img :src="logo" alt="ICT Week 2026 Uzbekistan" width="67" height="42" />
      </a>
      <nav ref="nav" class="nav" aria-label="Main">
        <a
          v-for="l in links"
          :key="l.label"
          :href="l.href"
          class="nav-link"
          :class="{ 'is-active': activeHref === l.href }"
          :aria-current="activeHref === l.href ? 'page' : undefined"
          @click="activateLink(l.href)"
        >{{ l.label }}</a>
      </nav>
      <div class="actions">
        <button type="button" class="lang">
          English
          <svg width="16" height="16" viewBox="0 0 16 16" fill="none" aria-hidden="true">
            <path d="M4 6l4 4 4-4" stroke="#a4a7ae" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round" />
          </svg>
        </button>
        <a href="#register" class="cta">Register now</a>
        <button
          type="button"
          class="burger"
          :class="{ 'is-open': mobileMenuOpen }"
          :aria-label="mobileMenuOpen ? 'Close menu' : 'Open menu'"
          :aria-expanded="mobileMenuOpen"
          aria-controls="mobile-menu"
          @click="toggleMobileMenu"
        >
          <span></span><span></span><span></span>
        </button>
      </div>
    </div>
    <Transition name="mobile-menu">
      <nav v-if="mobileMenuOpen" id="mobile-menu" class="mobile-nav" aria-label="Mobile navigation">
        <a
          v-for="l in links"
          :key="l.label"
          :href="l.href"
          class="mobile-nav-link"
          :class="{ 'is-active': activeHref === l.href }"
          :aria-current="activeHref === l.href ? 'page' : undefined"
          @click="activateLink(l.href); closeMobileMenu()"
        >{{ l.label }}</a>
        <button type="button" class="mobile-lang">
          English
          <svg width="16" height="16" viewBox="0 0 16 16" fill="none" aria-hidden="true">
            <path d="M4 6l4 4 4-4" stroke="#a4a7ae" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round" />
          </svg>
        </button>
      </nav>
    </Transition>
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
  position: relative;
  isolation: isolate;
  width: 1040px;
  height: 80px;
  margin: 0 auto;
  display: flex;
  align-items: center;
  padding: 0 14px 0 32px;
  overflow: hidden;
  border-radius: 999px;
  background: rgba(255, 255, 255, 0.05);
  box-shadow: var(--glass-shadow);
  -webkit-backdrop-filter: blur(18px) saturate(125%);
  backdrop-filter: blur(18px) saturate(125%);
}

.brand {
  flex: none;
}

.brand img {
  width: 67px;
  height: 42px;
}

.nav {
  --indicator-x: 0px;
  --indicator-y: 0px;
  --indicator-width: 0px;
  --indicator-height: 0px;
  position: relative;
  display: flex;
  align-items: center;
  gap: 24px;
  margin-left: 138px;
}

.nav::before {
  position: absolute;
  top: 0;
  left: 0;
  width: var(--indicator-width);
  height: var(--indicator-height);
  border-radius: 999px;
  background:
    radial-gradient(ellipse at 50% 0%, rgba(132, 255, 193, 0.1), transparent 100%),
    linear-gradient(180deg, rgba(132, 255, 193, 0.05), rgba(132, 255, 193, 0.04)),
    #01141a;
  box-shadow: inset 0 0 0 1px rgba(132, 255, 193, 0.08);
  -webkit-backdrop-filter: blur(11.3px);
  backdrop-filter: blur(11.3px);
  content: '';
  opacity: 0;
  transform: translate3d(var(--indicator-x), var(--indicator-y), 0);
  transition:
    transform 360ms cubic-bezier(0.22, 1, 0.36, 1),
    width 360ms cubic-bezier(0.22, 1, 0.36, 1),
    opacity 160ms ease;
}

.nav.has-indicator::before {
  opacity: 1;
}

.nav-link {
  position: relative;
  z-index: 1;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 52px;
  padding: 0;
  font-size: 16px;
  line-height: 20px;
  font-weight: 500;
  color: #b5b2b1;
  border-radius: 26px;
  transition:
    color 220ms ease,
    text-shadow 220ms ease;
}

.nav-link:hover,
.nav-link:focus-visible {
  color: rgba(255, 255, 255, 0.94);
}

.nav-link.is-active {
  padding: 0 24.5px;
  color: #fff;
}

.actions {
  margin-left: auto;
  display: flex;
  align-items: center;
  gap: 12px;
}

.lang {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 6px;
  width: 119px;
  height: 52px;
  padding: 0;
  border: 1px solid var(--glass-line);
  border-radius: 26px;
  background: rgba(6, 18, 23, 0.38);
  box-shadow:
    inset 0 1px 0 rgba(255, 255, 255, 0.055),
    0 10px 24px rgba(0, 0, 0, 0.12);
  -webkit-backdrop-filter: blur(10px) saturate(115%);
  backdrop-filter: blur(10px) saturate(115%);
  color: #b5b2b1;
  font-size: 16px;
  transition:
    border-color 220ms ease,
    background-color 220ms ease,
    transform 220ms ease;
}

.cta {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 148px;
  height: 52px;
  padding: 0;
  border-radius: 26px;
  background: linear-gradient(180deg, #84ffc1 0%, #459b6f 100%);
  box-shadow:
    inset 0 1px 0 rgba(255, 255, 255, 0.32),
    0 12px 28px rgba(69, 155, 111, 0.16);
  color: #121b26;
  font-size: 16px;
  font-weight: 500;
  transition:
    filter 220ms ease,
    transform 220ms ease,
    box-shadow 220ms ease;
}

.lang:hover,
.lang:focus-visible {
  background-color: rgba(255, 255, 255, 0.05);
  transform: translateY(-1px);
}

.cta:hover,
.cta:focus-visible {
  filter: brightness(1.06);
  transform: translateY(-1px);
  box-shadow:
    0 10px 24px rgba(69, 155, 111, 0.2);
}

.nav-link:focus-visible,
.lang:focus-visible,
.cta:focus-visible,
.burger:focus-visible {
  outline: 2px solid #84ffc1;
  outline-offset: 3px;
}

.burger {
  display: none;
}

.mobile-nav {
  display: none;
}

@media (max-width: 1199px) {
  .header {
    top: 32px;
  }

  .bar {
    width: calc(100% - 48px);
    height: 58px;
    padding: 0 10px 0 16px;
    border-radius: 999px;
  }

  .brand img {
    width: 64px;
    height: auto;
  }

  .nav {
    margin-left: 88px;
    gap: 2px;
  }

  .nav-link {
    height: 36px;
    padding: 8px 12px;
    font-size: 14px;
    line-height: 20px;
  }

  .nav-link.is-active {
    padding: 0 12px;
  }

  .lang {
    width: auto;
    height: 38px;
    padding: 0 12px;
    font-size: 14px;
  }

  .cta {
    width: auto;
    height: 38px;
    padding: 0 18px;
    font-size: 14px;
  }

  .actions {
    gap: 10px;
  }
}

@media (max-width: 760px) and (min-width: 600px) {
  .nav {
    margin-left: 40px;
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
    background: rgba(2, 14, 16, 0.72);
    box-shadow:
      inset 0 -1px 0 var(--glass-line),
      0 12px 30px rgba(0, 0, 0, 0.16);
  }

  .brand img {
    width: 62px;
    height: auto;
  }

  .nav,
  .lang {
    display: none;
  }

  .cta {
    width: auto;
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
    border: 1px solid var(--glass-line);
    border-radius: 8px;
    background: var(--glass-card);
    box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.055);
  }

  .burger span {
    height: 2px;
    border-radius: 1px;
    background: #fff;
    transform-origin: center;
    transition:
      transform 180ms ease,
      opacity 180ms ease;
  }

  .burger.is-open span:nth-child(1) {
    transform: translateY(7px) rotate(45deg);
  }

  .burger.is-open span:nth-child(2) {
    opacity: 0;
  }

  .burger.is-open span:nth-child(3) {
    transform: translateY(-7px) rotate(-45deg);
  }

  .mobile-nav {
    position: absolute;
    top: 72px;
    left: 12px;
    right: 12px;
    display: flex;
    flex-direction: column;
    gap: 4px;
    padding: 10px;
    border: 1px solid rgba(255, 255, 255, 0.1);
    border-radius: 16px;
    background: rgba(6, 18, 23, 0.88);
    box-shadow:
      inset 0 1px 0 rgba(255, 255, 255, 0.06),
      0 18px 40px rgba(0, 0, 0, 0.42);
    -webkit-backdrop-filter: blur(18px);
    backdrop-filter: blur(18px);
  }

  .mobile-nav-link,
  .mobile-lang {
    display: flex;
    align-items: center;
    min-height: 46px;
    padding: 0 16px;
    border-radius: 12px;
    color: #b5b2b1;
    font-size: 15px;
    font-weight: 500;
  }

  .mobile-nav-link.is-active {
    background: rgba(132, 255, 193, 0.1);
    color: #fff;
  }

  .mobile-lang {
    justify-content: space-between;
    width: 100%;
    border-top: 1px solid rgba(255, 255, 255, 0.08);
    border-radius: 0 0 12px 12px;
  }

  .mobile-menu-enter-active,
  .mobile-menu-leave-active {
    transition:
      opacity 180ms ease,
      transform 180ms ease;
  }

  .mobile-menu-enter-from,
  .mobile-menu-leave-to {
    opacity: 0;
    transform: translateY(-8px);
  }
}

@media (prefers-reduced-motion: reduce) {
  .nav::before,
  .nav-link,
  .lang,
  .cta,
  .burger span,
  .mobile-menu-enter-active,
  .mobile-menu-leave-active {
    transition-duration: 0.01ms;
  }
}
</style>
