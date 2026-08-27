<script setup>
import { ref } from 'vue'
import SelectField from './SelectField.vue'

const countries = [
  'Uzbekistan', 'Kazakhstan', 'Kyrgyzstan', 'Tajikistan', 'Turkmenistan', 'Azerbaijan',
  'Turkey', 'United Arab Emirates', 'Saudi Arabia', 'Qatar', 'India', 'China', 'South Korea',
  'Japan', 'Singapore', 'Germany', 'France', 'Netherlands', 'United Kingdom', 'United States', 'Other'
]
const categories = ['Startup founder', 'Investor', 'Corporate representative', 'Government official', 'Media', 'Student', 'Other']
const tracks = [
  'Enterprise Uzbekistan Summit', 'Startup & Venture Summit', 'Tech & Service Outsourcing Conference',
  'Global Bridge', 'GameDev Conference', 'AI Native: Ideas to Innovation'
]
const sources = [
  'Online Advertisement (Instagram, Facebook, LinkedIn, Google)', 'Partner Network',
  'IT Park Representative', 'Organic Search / Website'
]

const agreed = ref(false)
const submitted = ref(false)

const submit = () => {
  submitted.value = true
}
</script>

<template>
  <section id="register" class="register">
    <div class="panel">
      <h2>Register for ICTWEEK Uzbekistan 2026</h2>
      <p class="sub">
        Join global tech leaders, enterprise delegates, and investors in Tashkent.<br />
        Complete your details below to secure your pass.
      </p>
      <form class="form" novalidate @submit.prevent="submit">
        <label class="field">
          <span class="label">Full name</span>
          <input type="text" name="name" placeholder="e.g. John Doe" autocomplete="name" />
        </label>
        <SelectField label="Country" placeholder="Select country..." :options="countries" />
        <label class="field">
          <span class="label">Email</span>
          <input type="email" name="email" placeholder="e.g. alex@company.com" autocomplete="email" />
        </label>
        <label class="field">
          <span class="label">Phone number</span>
          <input type="tel" name="phone" placeholder="e.g. +1 (555) 019-2834" autocomplete="tel" />
        </label>
        <label class="field">
          <span class="label">Company</span>
          <input type="text" name="company" placeholder="e.g. Tech Global Inc." autocomplete="organization" />
        </label>
        <label class="field">
          <span class="label">Position</span>
          <input type="text" name="position" placeholder="e.g. Managing Director" autocomplete="organization-title" />
        </label>
        <SelectField label="I am attending as" placeholder="Select category..." :options="categories" />
        <SelectField label="Event track(s) you plan to attend (Select all that apply)" placeholder="Select track(s)..." :options="tracks" multiple />
        <SelectField label="How did you hear about us?" placeholder="Select source..." :options="sources" />
        <label class="field">
          <span class="label">Name of focal point in IT Park (if available)</span>
          <input type="text" name="focal" placeholder="e.g. Contact person or team member name" />
        </label>
        <label class="consent">
          <input v-model="agreed" type="checkbox" name="consent" />
          <span class="box" aria-hidden="true">
            <svg width="12" height="10" viewBox="0 0 12 10" fill="none">
              <path d="M1.5 5l3 3L10.5 1.5" stroke="#0b1a14" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round" />
            </svg>
          </span>
          <span class="consent-text">
            Yes, I agree that IT Park Uzbekistan team may contact me by e-mail to inquire about my
            request, and I am aware that my shared personal data will be saved. This consent can be
            withdrawn at any time.
          </span>
        </label>
        <div class="actions">
          <span v-if="submitted" class="done">Thank you! Your application has been received.</span>
          <button type="submit" class="btn">
            <span class="v-dt">Register now
              <svg width="16" height="16" viewBox="0 0 16 16" fill="none" aria-hidden="true">
                <path d="M4.5 11.5l7-7M6 4.5h5.5V10" stroke="currentColor" stroke-width="1.6" stroke-linecap="round" stroke-linejoin="round" />
              </svg>
            </span>
            <span class="v-m">Submit Application</span>
          </button>
        </div>
      </form>
    </div>
  </section>
</template>

<style scoped>
.register {
  margin-top: 20px;
  padding-bottom: 60px;
}

.panel {
  width: 1275px;
  margin-left: 85px;
  padding: 98px 52px 24px;
  border-radius: 28px;
  background: #051315;
}

h2 {
  text-align: center;
  font-size: 48px;
  font-weight: 600;
  letter-spacing: -0.5px;
}

.sub {
  margin-top: 16px;
  text-align: center;
  font-size: 18px;
  line-height: 28px;
  color: #aab3b3;
}

.form {
  display: grid;
  grid-template-columns: 1fr 1fr;
  column-gap: 32px;
  row-gap: 14px;
  margin-top: 26px;
}

.field {
  display: flex;
  flex-direction: column;
  gap: 8px;
}

.label {
  font-size: 14px;
  line-height: 1.2;
  font-weight: 600;
}

input[type='text'],
input[type='email'],
input[type='tel'] {
  height: 46px;
  padding: 0 16px;
  border: 1px solid rgba(255, 255, 255, 0.16);
  border-radius: 10px;
  background: rgba(13, 24, 30, 0.85);
  color: #fff;
  font-size: 15px;
}

input::placeholder {
  color: #8b9494;
}

input:focus-visible,
:deep(.control:focus-visible) {
  outline: 2px solid #63ca96;
  outline-offset: 1px;
}

.consent {
  grid-column: 1 / -1;
  display: flex;
  align-items: flex-start;
  gap: 14px;
  margin-top: 18px;
  cursor: pointer;
}

.consent input {
  position: absolute;
  opacity: 0;
  pointer-events: none;
}

.box {
  flex: none;
  display: flex;
  align-items: center;
  justify-content: center;
  width: 20px;
  height: 20px;
  margin-top: 2px;
  border: 1.5px solid rgba(255, 255, 255, 0.5);
  border-radius: 5px;
  background: transparent;
}

.box svg {
  opacity: 0;
}

.consent input:checked + .box {
  background: #84ffc1;
  border-color: #84ffc1;
}

.consent input:checked + .box svg {
  opacity: 1;
}

.consent-text {
  font-size: 16px;
  line-height: 25px;
  color: #dfe4e4;
}

.actions {
  grid-column: 1 / -1;
  display: flex;
  align-items: center;
  justify-content: flex-end;
  gap: 24px;
  margin-top: 20px;
}

.done {
  color: #84ffc1;
  font-size: 15px;
  font-weight: 600;
}

.btn {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  height: 52px;
  padding: 0 26px;
  border-radius: 12px;
  background: #84ffc1;
  color: #121b26;
  font-size: 16px;
  font-weight: 600;
}

.btn .v-dt {
  display: inline-flex;
  align-items: center;
  gap: 8px;
}

.v-m {
  display: none;
}

@media (max-width: 1199px) {
  .register {
    margin-top: 46px;
    padding-bottom: 32px;
  }

  .panel {
    width: calc(100% - 72px);
    margin: 0 auto;
    padding: 30px 20px 18px;
    border-radius: 20px;
  }

  h2 {
    font-size: 30px;
  }

  .sub {
    margin-top: 10px;
    font-size: 14px;
    line-height: 22px;
  }

  .form {
    column-gap: 24px;
    row-gap: 10px;
    margin-top: 26px;
  }

  .field {
    gap: 6px;
  }

  input[type='text'],
  input[type='email'],
  input[type='tel'] {
    height: 38px;
  }

  :deep(.control) {
    height: 38px;
  }

  .consent {
    margin-top: 14px;
  }

  .actions {
    margin-top: 10px;
  }

  .btn {
    height: 48px;
  }

  .consent-text {
    font-size: 14px;
    line-height: 22px;
  }
}

@media (max-width: 599px) {
  .register {
    padding-bottom: 32px;
  }

  .panel {
    width: 100%;
    padding: 28px 16px 22px;
    border-radius: 0;
    background: transparent;
  }

  h2 {
    font-size: 26px;
  }

  .sub {
    font-size: 14px;
    line-height: 21px;
  }

  .sub br {
    display: none;
  }

  .form {
    grid-template-columns: 1fr;
    row-gap: 11px;
    margin-top: 22px;
  }

  .field {
    gap: 4px;
  }

  .consent {
    margin-top: 12px;
    gap: 12px;
  }

  .box {
    border-radius: 50%;
  }

  .consent-text {
    font-size: 13.5px;
    line-height: 20px;
  }

  .actions {
    margin-top: 16px;
  }

  .btn {
    width: 100%;
    justify-content: center;
    height: 54px;
    border-radius: 14px;
  }

  .btn .v-dt {
    display: none;
  }

  .v-m {
    display: inline;
  }
}
</style>
