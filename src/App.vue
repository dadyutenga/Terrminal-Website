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
            <div class="architecture__stack">
              <div class="architecture__code">
                <CodeBlock :lines="architectureLines" />
              </div>
              <div class="architecture__schematic">
                <header>
                  <h3>Signal spine</h3>
                  <p>Latency fields mapped across every operative module.</p>
                </header>
                <div class="schematic__timeline">
                  <div v-for="node in architectureNodes" :key="node.label" class="schematic__node">
                    <span class="schematic__label">{{ node.label }}</span>
                    <span class="schematic__meta">{{ node.meta }}</span>
                    <span class="schematic__metric">{{ node.metric }}</span>
                  </div>
                </div>
              </div>
            </div>
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
              <div class="architecture__stream">
                <div class="architecture__stream-item" v-for="stream in telemetryStream" :key="stream.label">
                  <span>{{ stream.label }}</span>
                  <strong>{{ stream.value }}</strong>
                </div>
              </div>
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
              <div class="live-demo__telemetry">
                <div class="telemetry__column">
                  <span class="telemetry__label">Signal sync</span>
                  <strong>99.7%</strong>
                  <small>mesh coherence</small>
                </div>
                <div class="telemetry__column">
                  <span class="telemetry__label">Command rate</span>
                  <strong>412/min</strong>
                  <small>peak sustained</small>
                </div>
                <div class="telemetry__column">
                  <span class="telemetry__label">Thermal band</span>
                  <strong>41°C</strong>
                  <small>active cooling</small>
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>
      <SignalMatrix />
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
import SignalMatrix from './components/SignalMatrix.vue';

const architectureLines = [
  "module TerminalAgent {",
  "  gateway CommandRouter {",
  "    listen 'stdin' -> dispatch -> cognition.mesh();",
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
  "    schedule cron('*/5 * * * *');",
  '    route -> plugins.sync();',
  '  }',
  '}'
];

const architectureNodes = [
  { label: 'Ingress', meta: 'stdin://', metric: '0.21ms' },
  { label: 'Router', meta: 'dispatch.bus', metric: '0.38ms' },
  { label: 'Cognition', meta: 'mesh[x8]', metric: '6.1ms' },
  { label: 'Execution', meta: 'sandbox.vm', metric: '3.7ms' },
  { label: 'Telemetry', meta: 'stream::audit', metric: '1.5ms' },
  { label: 'Automation', meta: 'cron://sync', metric: '0.9ms' }
];

const telemetryStream = [
  { label: 'command.qps', value: '7.2' },
  { label: 'mesh.packets', value: '54k/s' },
  { label: 'uptime', value: '418h' }
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
  grid-template-columns: 1.25fr 0.75fr;
  align-items: stretch;
  gap: 3.5rem;
  background: linear-gradient(140deg, rgba(6, 9, 18, 0.94), rgba(10, 16, 36, 0.6));
  border: 1px solid rgba(41, 240, 255, 0.12);
  padding: 3.5rem;
  position: relative;
  clip-path: polygon(0 0, 94% 0, 100% 14%, 100% 100%, 6% 100%, 0 86%);
  box-shadow: 0 40px 90px rgba(0, 6, 25, 0.75);
}

.architecture__content::after {
  content: '';
  position: absolute;
  inset: 0;
  background: linear-gradient(135deg, rgba(41, 240, 255, 0.1), transparent 60%);
  mix-blend-mode: screen;
  pointer-events: none;
}

.architecture__stack {
  display: grid;
  grid-template-rows: minmax(0, 1fr) auto;
  gap: 2.5rem;
  position: relative;
}

.architecture__stack::before {
  content: '';
  position: absolute;
  inset: 4% 8%;
  border: 1px solid rgba(41, 240, 255, 0.08);
  pointer-events: none;
  mask-image: linear-gradient(180deg, transparent, #fff 12%, #fff 88%, transparent);
  z-index: 0;
}

.architecture__stack > * {
  position: relative;
  z-index: 1;
}

.architecture__schematic {
  position: relative;
  padding: 1.6rem 1.8rem;
  background: linear-gradient(120deg, rgba(11, 16, 36, 0.92), rgba(21, 28, 54, 0.55));
  border: 1px solid rgba(41, 240, 255, 0.16);
  clip-path: polygon(0 0, 90% 0, 100% 22%, 100% 100%, 12% 100%, 0 82%);
  overflow: hidden;
}

.architecture__schematic::before {
  content: '';
  position: absolute;
  inset: 0;
  background-image: radial-gradient(circle at 20% 20%, rgba(41, 240, 255, 0.18), transparent 58%),
    linear-gradient(90deg, rgba(41, 240, 255, 0.08) 1px, transparent 1px);
  background-size: 100% 100%, 32px;
  opacity: 0.35;
  mix-blend-mode: screen;
  pointer-events: none;
}

.architecture__schematic header {
  position: relative;
  display: grid;
  gap: 0.5rem;
  margin-bottom: 1.8rem;
  text-transform: uppercase;
  letter-spacing: 0.14em;
}

.architecture__schematic h3 {
  font-family: 'IBM Plex Mono', monospace;
  font-size: 0.88rem;
}

.architecture__schematic p {
  font-size: 0.75rem;
  color: rgba(146, 160, 196, 0.7);
  text-transform: none;
  letter-spacing: 0.04em;
}

.schematic__timeline {
  position: relative;
  display: grid;
  gap: 1.2rem;
  padding-left: 1.8rem;
}

.schematic__timeline::before {
  content: '';
  position: absolute;
  left: 0.45rem;
  top: 0.2rem;
  bottom: 0.2rem;
  background: linear-gradient(180deg, rgba(41, 240, 255, 0.4), rgba(154, 92, 255, 0.2));
  width: 2px;
}

.schematic__node {
  display: grid;
  gap: 0.15rem;
  position: relative;
  padding-left: 1.2rem;
  font-family: 'IBM Plex Mono', monospace;
}

.schematic__node::before {
  content: '';
  position: absolute;
  left: -1.1rem;
  top: 0.35rem;
  width: 0.65rem;
  height: 0.65rem;
  border-radius: 50%;
  background: radial-gradient(circle, rgba(41, 240, 255, 0.9), rgba(41, 240, 255, 0) 70%);
  box-shadow: 0 0 18px rgba(41, 240, 255, 0.65);
}

.schematic__label {
  text-transform: uppercase;
  letter-spacing: 0.18em;
  font-size: 0.7rem;
  color: rgba(246, 247, 255, 0.82);
}

.schematic__meta {
  font-size: 0.75rem;
  color: rgba(154, 173, 210, 0.75);
}

.schematic__metric {
  font-size: 0.85rem;
  color: var(--accent-primary);
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

.architecture__stream {
  margin-top: 2.5rem;
  display: grid;
  gap: 1rem;
  padding: 1.5rem 1.6rem;
  background: rgba(9, 12, 24, 0.78);
  border: 1px solid rgba(41, 240, 255, 0.12);
  clip-path: polygon(0 0, 92% 0, 100% 18%, 100% 100%, 10% 100%, 0 82%);
  position: relative;
  overflow: hidden;
}

.architecture__stream::before {
  content: '';
  position: absolute;
  inset: 0;
  background: linear-gradient(100deg, rgba(154, 92, 255, 0.16), transparent 60%);
  mix-blend-mode: screen;
  opacity: 0.75;
  pointer-events: none;
}

.architecture__stream-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  font-family: 'IBM Plex Mono', monospace;
  text-transform: uppercase;
  letter-spacing: 0.12em;
  font-size: 0.7rem;
  position: relative;
}

.architecture__stream-item strong {
  color: var(--accent-primary);
  font-size: 0.9rem;
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
  position: relative;
  overflow: hidden;
}

.live-demo__note::before {
  content: '';
  position: absolute;
  inset: 0;
  background-image: linear-gradient(135deg, rgba(41, 240, 255, 0.08), transparent 65%),
    linear-gradient(0deg, rgba(41, 240, 255, 0.06) 1px, transparent 1px);
  background-size: 100% 100%, 100% 18px;
  opacity: 0.8;
  mix-blend-mode: screen;
  pointer-events: none;
}

.live-demo__telemetry {
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  gap: 1.5rem;
  position: relative;
  z-index: 1;
}

.telemetry__column {
  display: grid;
  gap: 0.2rem;
  text-transform: uppercase;
  letter-spacing: 0.12em;
  font-size: 0.65rem;
}

.telemetry__column strong {
  font-size: 1.1rem;
  color: var(--accent-primary);
}

.telemetry__column small {
  letter-spacing: 0.08em;
  color: rgba(146, 160, 196, 0.7);
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

  .live-demo__telemetry {
    grid-template-columns: repeat(auto-fit, minmax(160px, 1fr));
  }
}

@media (max-width: 768px) {
  .architecture__content {
    padding: 2.5rem;
  }

  .live-demo__body {
    gap: 2rem;
  }

  .architecture__schematic {
    padding: 1.4rem 1.5rem;
  }
}

@media (max-width: 640px) {
  main {
    gap: 5rem;
    padding-top: 4rem;
  }

  .architecture__content {
    padding: 2rem 1.6rem;
    gap: 2rem;
  }

  .architecture__stack {
    gap: 2rem;
  }

  .architecture__schematic {
    clip-path: polygon(0 0, 88% 0, 100% 24%, 100% 100%, 14% 100%, 0 78%);
  }

  .live-demo__note {
    padding: 2rem;
  }
}
</style>
