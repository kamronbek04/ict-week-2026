<script setup>
import photo from '../assets/save-photo.webp'
</script>

<template>
  <section class="save">
    <div class="panel">
      <div class="copy">
        <h2>Save your spot today!</h2>
        <p>
          Every unicorn starts as a single star.<br />
          Together they become the Northern Lights.
        </p>
        <p>
          Welcome to Uzbekistan, where visionary government support and a
          thriving innovation ecosystem help founders turn bold ideas into
          global ventures.
        </p>
        <p>
          Here, startups and tech companies don&rsquo;t just become part of the
          Northern Lights&mdash;they discover their North Star and follow it all
          the way to international success.
        </p>
        <a href="#register" class="btn">
          Register now
          <svg width="16" height="16" viewBox="0 0 16 16" fill="none" aria-hidden="true">
            <path d="M4.5 11.5l7-7M6 4.5h5.5V10" stroke="currentColor" stroke-width="1.6" stroke-linecap="round" stroke-linejoin="round" />
          </svg>
        </a>
      </div>
      <img class="photo" :src="photo" alt="ICT Week conference hall during a keynote" width="570" height="414" loading="lazy" />
    </div>
  </section>
</template>

<style scoped>
.save {
  margin-top: 45px;
}

.panel {
  width: 1280px;
  margin-left: 80px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 37px 35px 33px 37px;
  border-radius: 24px;
  background: var(--glass-panel);
  box-shadow: var(--glass-shadow);
  -webkit-backdrop-filter: var(--glass-filter);
  backdrop-filter: var(--glass-filter);
}

.copy {
  max-width: 600px;
}

h2 {
  font-size: 48px;
  line-height: 1.2;
  font-weight: 600;
  letter-spacing: -0.5px;
}

p {
  margin-top: 28px;
  font-size: 17px;
  line-height: 29px;
  color: #ccd3d3;
}

p + p {
  margin-top: 22px;
}

.btn {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  height: 50px;
  padding: 0 24px;
  margin-top: 36px;
  border-radius: 12px;
  background: #84ffc1;
  color: #121b26;
  font-size: 16px;
  font-weight: 600;
}

.photo {
  flex: none;
  border-radius: 12px;
}

@media (max-width: 1199px) {
  .save {
    margin-top: 46px;
  }

  .panel {
    width: calc(100% - 72px);
    margin: 0 auto;
    flex-direction: column-reverse;
    align-items: stretch;
    gap: 18px;
    padding: 20px 20px 26px;
    border-radius: 20px;
  }

  .copy {
    max-width: none;
    padding: 0 2px;
  }

  p br {
    display: none;
  }

  h2 {
    font-size: 38px;
  }

  p {
    margin-top: 18px;
    font-size: 16px;
    line-height: 26px;
  }

  p + p {
    margin-top: 14px;
  }

  .btn {
    margin-top: 24px;
  }

  .photo {
    width: 100%;
    height: 330px;
    object-fit: cover;
  }
}

@media (max-width: 599px) {
  .save {
    margin-top: 36px;
  }

  p br {
    display: inline;
  }

  .panel {
    width: calc(100% - 32px);
    padding: 14px 14px 20px;
    gap: 18px;
    border-radius: 16px;
  }

  h2 {
    font-size: 30px;
  }

  p {
    font-size: 15px;
    line-height: 24px;
  }

  .btn {
    width: 100%;
    justify-content: center;
  }

  .photo {
    height: 212px;
  }
}
</style>
