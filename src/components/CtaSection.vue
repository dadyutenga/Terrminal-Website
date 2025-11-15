<template>
  <section class="cta" id="cta">
    <div class="container-frame cta__frame">
      <div class="cta__content">
        <span class="section-heading">Initiate</span>
        <h2>Launch Terminal Agent</h2>
        <p>
          Engage the command line intelligence layer engineered for elite developer operations. Precision execution,
          automation, and cognition in one console.
        </p>
        <div class="cta__actions">
          <button class="cta__button glow-border">Open Console</button>
          <a href="#demo" class="cta__link">View live demo</a>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup></script>

<style scoped>
.cta {
  position: relative;
}

.cta::before {
  content: '';
  position: absolute;
  inset: 0;
  background: linear-gradient(145deg, rgba(41, 240, 255, 0.12), transparent 60%);
  opacity: 0.6;
}

.cta__frame {
  position: relative;
  padding-bottom: 4rem;
}

.cta__content {
  position: relative;
  padding: 3.5rem 3rem;
  border: 1px solid rgba(41, 240, 255, 0.16);
  background: rgba(10, 12, 22, 0.88);
  clip-path: polygon(0 0, 90% 0, 100% 18%, 100% 100%, 12% 100%, 0 84%);
  display: grid;
  gap: 1.6rem;
  text-transform: uppercase;
  letter-spacing: 0.14em;
}

.cta__content h2 {
  font-size: clamp(2rem, 4vw, 2.8rem);
  font-weight: 700;
}

.cta__content p {
  text-transform: none;
  letter-spacing: 0.02em;
  font-family: 'IBM Plex Mono', monospace;
  line-height: 1.7;
  color: var(--text-muted);
}

.cta__actions {
  display: flex;
  gap: 1.5rem;
  flex-wrap: wrap;
}

.cta__button {
  padding: 1rem 2.5rem;
  border: 1px solid rgba(41, 240, 255, 0.4);
  background: rgba(9, 12, 24, 0.9);
  text-transform: uppercase;
  font-size: 0.9rem;
  letter-spacing: 0.18em;
  font-family: 'IBM Plex Mono', monospace;
  transition: transform 0.35s ease, border 0.35s ease;
}

.cta__button:hover {
  transform: translateY(-3px);
  border-color: var(--accent-primary);
}

.cta__link {
  align-self: center;
  font-family: 'IBM Plex Mono', monospace;
  letter-spacing: 0.1em;
  color: var(--accent-primary);
  position: relative;
}

.cta__link::after {
  content: '';
  position: absolute;
  left: 0;
  bottom: -0.2rem;
  width: 100%;
  height: 1px;
  background: var(--accent-primary);
  transform: scaleX(0);
  transform-origin: left;
  transition: transform 0.3s ease;
}

.cta__link:hover::after {
  transform: scaleX(1);
}

@media (max-width: 640px) {
  .cta__content {
    padding: 2.5rem 2rem;
  }
}
</style>
