<template>
  <section class="hero" id="hero">
    <div class="container-frame hero__frame">
      <div class="hero__header">
        <div class="hero__title-block">
          <span class="section-heading">Terminal Agent</span>
          <h1 class="hero__headline">
            <span class="hero__glitch" aria-hidden="true">Hyper-Precise Terminal Intelligence</span>
            <span class="hero__text">Hyper-Precise Terminal Intelligence</span>
          </h1>
          <p class="hero__sub">
            Deploy an AI-native terminal that compiles, orchestrates, and executes with tactical clarity across your entire
            engineering stack.
          </p>
          <div class="hero__cta">
            <button class="hero__button glow-border" @mouseenter="triggerGlitch">
              <span>Open Terminal</span>
              <svg width="22" height="22" viewBox="0 0 22 22" fill="none" aria-hidden="true">
                <path d="M6 5L15 11L6 17" stroke="var(--accent-primary)" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" />
              </svg>
            </button>
            <div class="hero__cli caret">launch --mode hyperdrive</div>
          </div>
        </div>
        <div class="hero__orbital">
          <div class="hero__orbital-grid"></div>
          <div class="hero__orbital-core"></div>
          <div class="hero__orbital-ring" ref="ring"></div>
        </div>
      </div>
      <div class="hero__meta">
        <div class="hero__meta-item">
          <span>Latency</span>
          <strong>11.8ms</strong>
        </div>
        <div class="hero__meta-item">
          <span>Automation Graph</span>
          <strong>642 nodes</strong>
        </div>
        <div class="hero__meta-item">
          <span>Secure Sessions</span>
          <strong>256-bit sealed</strong>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { onMounted, ref } from 'vue';
import { gsap } from 'gsap';

const ring = ref(null);

const triggerGlitch = () => {
  gsap.fromTo(
    '.hero__glitch',
    { clipPath: 'inset(0 0 0 0)' },
    {
      clipPath: 'inset(0 0 0 0)',
      duration: 0.6,
      onStart: () => {
        gsap.to('.hero__glitch', {
          keyframes: [
            { x: 0, filter: 'hue-rotate(0deg)' },
            { x: 8, skewX: 2, filter: 'hue-rotate(45deg)', duration: 0.08 },
            { x: -6, skewX: -2, filter: 'hue-rotate(-45deg)', duration: 0.08 },
            { x: 0, skewX: 0, filter: 'hue-rotate(0deg)', duration: 0.1 }
          ]
        });
      }
    }
  );
};

onMounted(() => {
  gsap.from('.hero__headline', { y: 60, opacity: 0, duration: 1.1, ease: 'power3.out' });
  gsap.from('.hero__sub', { y: 40, opacity: 0, duration: 1, delay: 0.3, ease: 'power2.out' });
  gsap.from('.hero__button', { y: 30, opacity: 0, duration: 0.9, delay: 0.5 });
  gsap.from('.hero__cli', { y: 30, opacity: 0, duration: 0.9, delay: 0.6 });
  gsap.to(ring.value, {
    rotate: 360,
    repeat: -1,
    duration: 18,
    ease: 'none'
  });
});
</script>

<style scoped>
.hero {
  position: relative;
  padding-top: 4rem;
}

.hero__frame {
  display: flex;
  flex-direction: column;
  gap: 4rem;
}

.hero__header {
  display: grid;
  grid-template-columns: 1.15fr 0.85fr;
  gap: 3.5rem;
  align-items: center;
}

.hero__title-block {
  position: relative;
  z-index: 3;
}

.hero__headline {
  font-size: clamp(2.8rem, 6vw, 4.5rem);
  line-height: 1.05;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.08em;
  position: relative;
}

.hero__glitch {
  position: absolute;
  inset: 0;
  color: var(--accent-secondary);
  clip-path: inset(0 0 0 0);
  mix-blend-mode: screen;
  opacity: 0.38;
  pointer-events: none;
}

.hero__text {
  display: inline-block;
  background: linear-gradient(90deg, var(--text-primary), rgba(41, 240, 255, 0.8));
  -webkit-background-clip: text;
  color: transparent;
}

.hero__sub {
  margin-top: 1.5rem;
  max-width: 38rem;
  line-height: 1.7;
  color: var(--text-muted);
  font-size: 1.05rem;
}

.hero__cta {
  display: flex;
  align-items: center;
  gap: 1.5rem;
  margin-top: 2.5rem;
}

.hero__button {
  display: inline-flex;
  align-items: center;
  gap: 0.75rem;
  padding: 0.9rem 1.8rem;
  border: 1px solid rgba(41, 240, 255, 0.4);
  background: rgba(9, 12, 24, 0.8);
  text-transform: uppercase;
  letter-spacing: 0.18em;
  font-size: 0.78rem;
  transition: transform 0.3s ease, border 0.3s ease;
  font-family: 'IBM Plex Mono', monospace;
}

.hero__button:hover {
  transform: translateY(-2px);
  border-color: var(--accent-primary);
}

.hero__cli {
  font-family: 'IBM Plex Mono', monospace;
  padding: 0.65rem 1rem;
  background: rgba(14, 18, 32, 0.85);
  border: 1px solid rgba(41, 240, 255, 0.2);
  text-transform: lowercase;
  letter-spacing: 0.04em;
  font-size: 0.9rem;
}

.hero__orbital {
  position: relative;
  width: min(420px, 100%);
  aspect-ratio: 1;
  margin-left: auto;
  isolation: isolate;
}

.hero__orbital-grid {
  position: absolute;
  inset: 12%;
  background: conic-gradient(from 180deg, rgba(41, 240, 255, 0.09), rgba(9, 12, 24, 0));
  mask-image: radial-gradient(circle, #000 55%, transparent 72%);
  border-radius: 50%;
  filter: blur(2px);
}

.hero__orbital-core {
  position: absolute;
  inset: 28%;
  background: radial-gradient(circle, rgba(41, 240, 255, 0.9), rgba(41, 240, 255, 0));
  border-radius: 50%;
  box-shadow: 0 0 30px rgba(41, 240, 255, 0.35);
}

.hero__orbital-ring {
  position: absolute;
  inset: 0;
  border: 1px solid rgba(41, 240, 255, 0.35);
  border-radius: 50%;
  box-shadow: 0 0 50px rgba(41, 240, 255, 0.35);
}

.hero__meta {
  display: flex;
  align-items: center;
  gap: clamp(1.5rem, 6vw, 5rem);
  font-family: 'IBM Plex Mono', monospace;
  letter-spacing: 0.12em;
  text-transform: uppercase;
}

.hero__meta-item {
  display: grid;
  gap: 0.4rem;
}

.hero__meta-item span {
  font-size: 0.75rem;
  color: rgba(146, 160, 196, 0.7);
}

.hero__meta-item strong {
  font-size: clamp(1rem, 2vw, 1.3rem);
}

@media (max-width: 1024px) {
  .hero__header {
    grid-template-columns: 1fr;
  }

  .hero__orbital {
    margin: 0 auto;
    width: min(360px, 70vw);
  }
}

@media (max-width: 640px) {
  .hero__meta {
    flex-direction: column;
    align-items: flex-start;
  }

  .hero__cta {
    flex-direction: column;
    align-items: flex-start;
  }

  .hero__cli {
    margin-left: 0;
  }
}
</style>
