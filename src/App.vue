<template>
  <div class="app-frame">
    <ScanlineOverlay />
    <main>
      <TerminalHero />
      <FeaturesSection />
      <section class="architecture" id="architecture">
        <div class="container-frame architecture__frame">
          <span class="section-heading">System Architecture</span>
          <div class="architecture__content">
            <CodeBlock :lines="architectureLines" />
            <div class="architecture__notes">
              <h3>Stacked for precision</h3>
              <p>
                Terminal Agent orchestrates deterministic execution pipelines and intelligent reasoning modules with
                microsecond observability.
              </p>
              <ul>
                <li>Deterministic command router</li>
                <li>Sandboxed execution core</li>
                <li>Adaptive cognition mesh</li>
                <li>Secure telemetry bus</li>
              </ul>
            </div>
          </div>
        </div>
      </section>
      <section class="live-demo" id="demo">
        <div class="container-frame live-demo__frame">
          <span class="section-heading">Live demo</span>
          <div class="live-demo__body">
            <TerminalWindow />
            <div class="live-demo__note">
              <h3>Precision CLI, augmented</h3>
              <p>
                Simulated prompt showcases the responsive intelligence of Terminal Agent. Commands stream in, insights stream out.
              </p>
            </div>
          </div>
        </div>
      </section>
      <CtaSection />
    </main>
  </div>
</template>

<script setup>
import TerminalHero from './components/TerminalHero.vue';
import FeaturesSection from './components/FeaturesSection.vue';
import TerminalWindow from './components/TerminalWindow.vue';
import CtaSection from './components/CtaSection.vue';
import ScanlineOverlay from './components/ScanlineOverlay.vue';
import CodeBlock from './components/CodeBlock.vue';

const architectureLines = [
  'module TerminalAgent {',
  '  gateway CommandRouter {',
  '    listen \'stdin\' -> dispatch -> cognition.mesh();',
  '  }',
  '  service CognitionMesh {',
  '    spin up "reasoning-nodes" x8;',
  '    enforce latency < 12ms;',
  '  }',
  '  service ExecutionCore {',
  '    sandbox docker::isolate();',
  '    audit stream::telemetry();',
  '  }',
  '  pipeline Automation {',
  '    schedule cron(\'*/5 * * * *\');',
  '    route -> plugins.sync();',
  '  }',
  '}'
];
</script>

<style scoped>
.app-frame {
  position: relative;
  min-height: 100vh;
  overflow-x: hidden;
  background: linear-gradient(130deg, rgba(3, 3, 8, 0.92), rgba(8, 12, 24, 0.92)), var(--bg-primary);
}

main {
  position: relative;
  display: flex;
  flex-direction: column;
  gap: 8rem;
  padding: 6rem 0 8rem;
}

.architecture__frame {
  padding: 0 0 4rem;
}

.architecture__content {
  display: grid;
  grid-template-columns: 1.1fr 0.9fr;
  align-items: start;
  gap: 3.5rem;
  background: linear-gradient(140deg, rgba(15, 18, 33, 0.88), rgba(5, 6, 16, 0.72));
  border: 1px solid rgba(41, 240, 255, 0.12);
  padding: 3rem;
  position: relative;
  clip-path: polygon(0 0, 96% 0, 100% 10%, 100% 100%, 4% 100%, 0 90%);
  box-shadow: 0 40px 80px rgba(1, 6, 18, 0.65);
}

.architecture__content::after {
  content: '';
  position: absolute;
  inset: 0;
  background: linear-gradient(135deg, rgba(41, 240, 255, 0.08), transparent 55%);
  mix-blend-mode: screen;
  pointer-events: none;
}

.architecture__notes h3 {
  font-size: clamp(1.5rem, 2vw, 2rem);
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.08em;
  margin-bottom: 1.5rem;
}

.architecture__notes p {
  color: var(--text-muted);
  line-height: 1.6;
  margin-bottom: 1.5rem;
}

.architecture__notes ul {
  font-family: 'IBM Plex Mono', monospace;
  display: grid;
  gap: 0.75rem;
  color: var(--text-primary);
}

.live-demo__frame {
  padding-bottom: 6rem;
}

.live-demo__body {
  display: grid;
  grid-template-columns: 1.2fr 0.8fr;
  align-items: stretch;
  gap: 2.5rem;
}

.live-demo__note {
  background: rgba(12, 16, 32, 0.65);
  border: 1px solid rgba(41, 240, 255, 0.1);
  padding: 2.5rem;
  display: flex;
  flex-direction: column;
  justify-content: center;
  gap: 1.5rem;
  font-family: 'IBM Plex Mono', monospace;
  letter-spacing: 0.03em;
}

.live-demo__note h3 {
  font-size: clamp(1.4rem, 1.8vw, 1.8rem);
  text-transform: uppercase;
  letter-spacing: 0.15em;
}

.live-demo__note p {
  color: var(--text-muted);
  line-height: 1.7;
}

@media (max-width: 1024px) {
  main {
    gap: 6rem;
    padding-top: 5rem;
  }

  .architecture__content,
  .live-demo__body {
    grid-template-columns: 1fr;
  }

  .architecture__content {
    gap: 2rem;
  }
}

@media (max-width: 640px) {
  main {
    gap: 5rem;
    padding-top: 4rem;
  }

  .architecture__content {
    padding: 2rem;
  }

  .live-demo__note {
    padding: 2rem;
  }
}
</style>
