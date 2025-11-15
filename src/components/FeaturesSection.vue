<template>
  <section class="features" id="features">
    <div class="container-frame features__frame">
      <span class="section-heading">Capabilities</span>
      <div class="features__grid">
        <article
          v-for="feature in features"
          :key="feature.title"
          class="features__card"
          @mouseenter="feature.onHover && feature.onHover()"
        >
          <div class="features__card-icon" v-html="feature.icon"></div>
          <h3>{{ feature.title }}</h3>
          <p>{{ feature.copy }}</p>
        </article>
      </div>
    </div>
  </section>
</template>

<script setup>
import { reactive } from 'vue';
import { gsap } from 'gsap';

const pulse = (selector) => {
  gsap.fromTo(
    selector,
    { boxShadow: '0 0 0 rgba(41, 240, 255, 0)' },
    {
      boxShadow: '0 0 35px rgba(41, 240, 255, 0.35)',
      duration: 0.6,
      yoyo: true,
      repeat: 1,
      ease: 'sine.out'
    }
  );
};

const features = reactive([
  {
    title: 'Code Execution',
    copy: 'Compile and run sandboxed workloads with deterministic feedback loops.',
    icon:
      '<svg width="52" height="52" viewBox="0 0 52 52" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M12 26L22 18V34L12 26Z" fill="none" stroke="var(--accent-primary)" stroke-width="2.4"/><rect x="26" y="14" width="14" height="24" rx="2" stroke="var(--accent-secondary)" stroke-width="2.4"/><path d="M26 20H40" stroke="var(--accent-primary)" stroke-width="2" stroke-linecap="round"/><path d="M26 26H40" stroke="var(--accent-primary)" stroke-width="2" stroke-linecap="round"/><path d="M26 32H40" stroke="var(--accent-primary)" stroke-width="2" stroke-linecap="round"/></svg>',
    onHover: () => pulse('.features__card:nth-child(1)')
  },
  {
    title: 'Intelligent Reasoning',
    copy: 'Multi-agent cognition mesh sequences reasoning chains in parallel.',
    icon:
      '<svg width="52" height="52" viewBox="0 0 52 52" fill="none" xmlns="http://www.w3.org/2000/svg"><circle cx="18" cy="26" r="8" stroke="var(--accent-primary)" stroke-width="2.4"/><circle cx="34" cy="18" r="6" stroke="var(--accent-secondary)" stroke-width="2.4"/><circle cx="34" cy="34" r="6" stroke="var(--accent-secondary)" stroke-width="2.4"/><path d="M24 22L30 20" stroke="var(--accent-primary)" stroke-width="2"/><path d="M24 30L30 32" stroke="var(--accent-primary)" stroke-width="2"/><path d="M34 24V28" stroke="var(--accent-secondary)" stroke-width="2"/></svg>',
    onHover: () => pulse('.features__card:nth-child(2)')
  },
  {
    title: 'Automation Pipelines',
    copy: 'Declarative pipelines orchestrate builds, deploys, and telemetry flows.',
    icon:
      '<svg width="52" height="52" viewBox="0 0 52 52" fill="none" xmlns="http://www.w3.org/2000/svg"><rect x="10" y="16" width="12" height="20" stroke="var(--accent-primary)" stroke-width="2.4"/><rect x="20" y="12" width="12" height="28" stroke="var(--accent-secondary)" stroke-width="2.4"/><rect x="30" y="18" width="12" height="16" stroke="var(--accent-primary)" stroke-width="2.4"/><path d="M16 26H36" stroke="var(--accent-secondary)" stroke-width="2.4"/><path d="M12 36H40" stroke="var(--accent-primary)" stroke-width="2" stroke-dasharray="4 6"/></svg>',
    onHover: () => pulse('.features__card:nth-child(3)')
  },
  {
    title: 'Secure Sandboxing',
    copy: 'Isolated execution cells with cryptographic sealing and audit trails.',
    icon:
      '<svg width="52" height="52" viewBox="0 0 52 52" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M18 16L26 10L34 16V24C34 30.6274 29.6274 36 23 36C16.3726 36 12 30.6274 12 24V16H18Z" stroke="var(--accent-primary)" stroke-width="2.4"/><circle cx="23" cy="24" r="6" stroke="var(--accent-secondary)" stroke-width="2.4"/><path d="M23 21V27" stroke="var(--accent-secondary)" stroke-width="2"/><path d="M20 24H26" stroke="var(--accent-secondary)" stroke-width="2"/></svg>',
    onHover: () => pulse('.features__card:nth-child(4)')
  },
  {
    title: 'CLI-Native Interactions',
    copy: 'Native terminal semantics with enriched context overlays and hints.',
    icon:
      '<svg width="52" height="52" viewBox="0 0 52 52" fill="none" xmlns="http://www.w3.org/2000/svg"><rect x="10" y="14" width="32" height="24" rx="2" stroke="var(--accent-primary)" stroke-width="2.4"/><path d="M16 32L22 26L16 20" stroke="var(--accent-secondary)" stroke-width="2.4" stroke-linecap="round" stroke-linejoin="round"/><path d="M26 32H36" stroke="var(--accent-primary)" stroke-width="2.4" stroke-linecap="round"/></svg>',
    onHover: () => pulse('.features__card:nth-child(5)')
  },
  {
    title: 'Plugin Ecosystem',
    copy: 'Extend with bespoke modules, container adapters, and introspection hooks.',
    icon:
      '<svg width="52" height="52" viewBox="0 0 52 52" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M20 16H16C13.7909 16 12 17.7909 12 20V32C12 34.2091 13.7909 36 16 36H20V16Z" stroke="var(--accent-primary)" stroke-width="2.4"/><path d="M20 16H32V36H20" stroke="var(--accent-secondary)" stroke-width="2.4"/><path d="M32 22H36C38.2091 22 40 23.7909 40 26V28C40 30.2091 38.2091 32 36 32H32V22Z" stroke="var(--accent-primary)" stroke-width="2.4"/></svg>',
    onHover: () => pulse('.features__card:nth-child(6)')
  }
]);
</script>

<style scoped>
.features {
  position: relative;
}

.features__frame {
  display: flex;
  flex-direction: column;
  gap: 3rem;
}

.features__grid {
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  gap: 1.6rem;
  position: relative;
}

.features__grid::before {
  content: '';
  position: absolute;
  inset: -2rem;
  background: radial-gradient(circle at 30% 30%, rgba(41, 240, 255, 0.08), transparent 70%);
  filter: blur(20px);
  pointer-events: none;
}

.features__card {
  position: relative;
  padding: 2.25rem;
  background: rgba(10, 14, 28, 0.82);
  border: 1px solid rgba(41, 240, 255, 0.16);
  display: grid;
  gap: 1.5rem;
  align-content: start;
  min-height: 260px;
  clip-path: polygon(0 0, 92% 0, 100% 12%, 100% 100%, 8% 100%, 0 88%);
  transition: transform 0.35s ease;
  overflow: hidden;
}

.features__card::after {
  content: '';
  position: absolute;
  inset: -1px;
  border: 1px solid rgba(154, 92, 255, 0.18);
  opacity: 0;
  transition: opacity 0.3s ease;
  mix-blend-mode: screen;
}

.features__card:hover {
  transform: translateY(-6px);
}

.features__card:hover::after {
  opacity: 1;
}

.features__card-icon svg {
  width: 3rem;
  height: 3rem;
}

.features__card h3 {
  font-family: 'IBM Plex Mono', monospace;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  font-size: 0.95rem;
}

.features__card p {
  color: var(--text-muted);
  line-height: 1.6;
  font-size: 0.95rem;
}

@media (max-width: 1024px) {
  .features__grid {
    grid-template-columns: repeat(2, minmax(0, 1fr));
  }
}

@media (max-width: 640px) {
  .features__grid {
    grid-template-columns: 1fr;
  }

  .features__card {
    min-height: auto;
  }
}
</style>
