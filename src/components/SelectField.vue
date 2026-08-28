<script setup>
import { ref, computed, onMounted, onBeforeUnmount } from 'vue'

const props = defineProps({
  label: { type: String, required: true },
  placeholder: { type: String, required: true },
  options: { type: Array, required: true },
  multiple: { type: Boolean, default: false }
})

const open = ref(false)
const selected = ref(props.multiple ? [] : '')
const root = ref(null)

const display = computed(() => {
  if (props.multiple) return selected.value.length ? selected.value.join(', ') : ''
  return selected.value
})

const pick = (opt) => {
  if (props.multiple) {
    const i = selected.value.indexOf(opt)
    i === -1 ? selected.value.push(opt) : selected.value.splice(i, 1)
  } else {
    selected.value = opt
    open.value = false
  }
}

const isPicked = (opt) => (props.multiple ? selected.value.includes(opt) : selected.value === opt)

const onOutside = (e) => {
  if (root.value && !root.value.contains(e.target)) open.value = false
}
onMounted(() => document.addEventListener('pointerdown', onOutside))
onBeforeUnmount(() => document.removeEventListener('pointerdown', onOutside))
</script>

<template>
  <div ref="root" class="field">
    <span class="label">{{ label }}</span>
    <button type="button" class="control" :aria-expanded="open" @click="open = !open">
      <span :class="display ? 'value' : 'placeholder'">{{ display || placeholder }}</span>
      <svg width="16" height="16" viewBox="0 0 16 16" fill="none" :class="{ flip: open }" aria-hidden="true">
        <path d="M4 6l4 4 4-4" stroke="#aeb6b6" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round" />
      </svg>
    </button>
    <ul v-if="open" class="menu" :class="{ scrollable: options.length > 8 }" role="listbox">
      <li v-for="opt in options" :key="opt">
        <button type="button" class="option" role="option" :aria-selected="isPicked(opt)" @click="pick(opt)">
          <span class="dot" :class="{ on: isPicked(opt) }"></span>
          {{ opt }}
        </button>
      </li>
    </ul>
  </div>
</template>

<style scoped>
.field {
  position: relative;
  min-width: 0;
  display: flex;
  flex-direction: column;
  gap: 8px;
}

.label {
  font-size: 14px;
  line-height: 1.2;
  font-weight: 600;
}

.control {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 12px;
  width: 100%;
  min-width: 0;
  height: 46px;
  padding: 0 16px;
  border: 1px solid rgba(255, 255, 255, 0.16);
  border-radius: 10px;
  background: var(--glass-input);
  box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.035);
  -webkit-backdrop-filter: blur(6px);
  backdrop-filter: blur(6px);
  text-align: left;
}

.control > span {
  min-width: 0;
}

.control > svg {
  flex: none;
}

.placeholder {
  color: #8b9494;
  font-size: 15px;
}

.value {
  color: #fff;
  font-size: 15px;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}

.flip {
  transform: rotate(180deg);
}

.menu {
  position: absolute;
  top: calc(100% + 6px);
  left: 0;
  right: 0;
  z-index: 20;
  list-style: none;
  padding: 6px 0;
  border: 1px solid rgba(255, 255, 255, 0.12);
  border-radius: 10px;
  background: rgba(7, 20, 25, 0.94);
  box-shadow: 0 18px 40px rgba(0, 0, 0, 0.5);
}

.menu.scrollable {
  max-height: 280px;
  overflow-y: auto;
  overscroll-behavior: contain;
  scrollbar-color: rgba(132, 255, 193, 0.45) transparent;
  scrollbar-width: thin;
}

.menu.scrollable::-webkit-scrollbar {
  width: 6px;
}

.menu.scrollable::-webkit-scrollbar-thumb {
  border-radius: 999px;
  background: rgba(132, 255, 193, 0.45);
}

.option {
  display: flex;
  align-items: center;
  gap: 12px;
  width: 100%;
  padding: 12px 16px;
  font-size: 15px;
  color: #eef1f1;
  text-align: left;
}

.option:hover {
  background: rgba(255, 255, 255, 0.05);
}

.dot {
  flex: none;
  width: 18px;
  height: 18px;
  border-radius: 50%;
  background: #fff;
  border: 5px solid #fff;
  box-shadow: inset 0 0 0 1px rgba(0, 0, 0, 0.2);
}

.dot.on {
  background: #2ecc8f;
  border-color: #fff;
}
</style>
