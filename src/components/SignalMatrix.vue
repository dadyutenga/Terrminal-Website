<template>
  <section class="signal-matrix" id="signals">
    <div class="container-frame signal-matrix__frame">
      <div class="signal-matrix__header">
        <span class="section-heading">Signal lattice</span>
        <h2>Quantum Operations Atlas</h2>
        <p>
          Observe the command spine radiating across ASIA's terminal intelligence. Every node broadcasts state, frequency, and
          thermal band with absolute transparency.
        </p>
      </div>
      <div class="signal-matrix__grid">
        <article class="signal-matrix__panel signal-matrix__panel--scan">
          <header>
            <h3>Live signal sweep</h3>
            <span>Last sync {{ sweepWindow }}</span>
          </header>
          <div class="signal-matrix__sweep">
            <div v-for="channel in sweep" :key="channel.name" class="sweep__row">
              <div class="sweep__meta">
                <span class="sweep__channel">{{ channel.name }}</span>
                <span class="sweep__status">{{ channel.status }}</span>
              </div>
              <div class="sweep__bar">
                <span :style="{ width: channel.amplitude }"></span>
              </div>
              <div class="sweep__value">{{ channel.amplitude }}</div>
            </div>
          </div>
        </article>
        <article class="signal-matrix__panel signal-matrix__panel--mesh">
          <header>
            <h3>Mesh topology</h3>
            <span>Active clusters: {{ meshCells.length }}</span>
          </header>
          <div class="mesh__grid">
            <div v-for="cell in meshCells" :key="cell.label" class="mesh__cell">
              <span class="mesh__label">{{ cell.label }}</span>
              <strong>{{ cell.value }}</strong>
              <span class="mesh__meta">{{ cell.meta }}</span>
            </div>
          </div>
        </article>
        <article class="signal-matrix__panel signal-matrix__panel--broadcast">
          <header>
            <h3>Broadcast cadence</h3>
            <span>Orbit cycle {{ broadcastCycle }}</span>
          </header>
          <div class="broadcast__timeline">
            <div v-for="pulse in broadcasts" :key="pulse.label" class="broadcast__pulse">
              <div class="broadcast__marker"></div>
              <div class="broadcast__body">
                <span class="broadcast__label">{{ pulse.label }}</span>
                <span class="broadcast__meta">{{ pulse.meta }}</span>
                <span class="broadcast__value">{{ pulse.value }}</span>
              </div>
            </div>
          </div>
        </article>
      </div>
    </div>
  </section>
</template>

<script setup>
const sweepWindow = '00:02:14';

const sweep = [
  { name: 'north.cluster', amplitude: '82%', status: 'stabilized' },
  { name: 'io-telemetry', amplitude: '64%', status: 'saturated' },
  { name: 'mesh.channel.4', amplitude: '91%', status: 'optimal' },
  { name: 'hyperbus', amplitude: '77%', status: 'synced' },
  { name: 'chronicle', amplitude: '58%', status: 'archiving' }
];

const meshCells = [
  { label: 'command', value: 'A3', meta: 'ingress flux' },
  { label: 'mesh node', value: 'X8', meta: 'reasoning array' },
  { label: 'executor', value: 'C1', meta: 'isolation bay' },
  { label: 'telemetry', value: 'R6', meta: 'spectral trace' },
  { label: 'plugins', value: 'P4', meta: 'extension rail' },
  { label: 'custodian', value: 'S2', meta: 'integrity ward' }
];

const broadcastCycle = '003';

const broadcasts = [
  { label: 'Ingress handshake', meta: 'latency 0.21ms', value: 'OK' },
  { label: 'Mesh consensus', meta: 'hash 8d39af', value: 'LOCKED' },
  { label: 'Sandbox status', meta: 'containers 8/8', value: 'SEALED' },
  { label: 'Automation dispatch', meta: 'pipelines 12', value: 'ON SCHEDULE' }
];
</script>

<style scoped>
.signal-matrix {
  position: relative;
}

.signal-matrix::before {
  content: '';
  position: absolute;
  inset: 0;
  background: radial-gradient(circle at 10% 0%, rgba(41, 240, 255, 0.18), transparent 60%),
    radial-gradient(circle at 90% 20%, rgba(154, 92, 255, 0.15), transparent 70%);
  opacity: 0.5;
  pointer-events: none;
}

.signal-matrix__frame {
  position: relative;
  display: grid;
  gap: 3.5rem;
}

.signal-matrix__header {
  max-width: 46rem;
  display: grid;
  gap: 1.2rem;
}

.signal-matrix__header h2 {
  font-size: clamp(2.4rem, 4vw, 3.5rem);
  letter-spacing: 0.2em;
  text-transform: uppercase;
  line-height: 1.1;
}

.signal-matrix__header p {
  font-family: 'IBM Plex Mono', monospace;
  letter-spacing: 0.04em;
  color: var(--text-muted);
  line-height: 1.8;
}

.signal-matrix__grid {
  position: relative;
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  gap: 2.5rem;
}

.signal-matrix__grid::before {
  content: '';
  position: absolute;
  inset: -3rem -4rem;
  background-image: linear-gradient(90deg, rgba(41, 240, 255, 0.08) 1px, transparent 1px),
    linear-gradient(0deg, rgba(41, 240, 255, 0.08) 1px, transparent 1px);
  background-size: 120px 120px;
  opacity: 0.4;
  mix-blend-mode: screen;
  pointer-events: none;
}

.signal-matrix__panel {
  position: relative;
  padding: 2.5rem;
  background: rgba(9, 12, 24, 0.78);
  border: 1px solid rgba(41, 240, 255, 0.14);
  clip-path: polygon(0 0, 88% 0, 100% 20%, 100% 100%, 12% 100%, 0 80%);
  display: grid;
  gap: 1.8rem;
  overflow: hidden;
}

.signal-matrix__panel::after {
  content: '';
  position: absolute;
  inset: 0;
  background: linear-gradient(135deg, rgba(41, 240, 255, 0.12), transparent 55%);
  opacity: 0.75;
  mix-blend-mode: screen;
  pointer-events: none;
}

.signal-matrix__panel header {
  position: relative;
  display: flex;
  justify-content: space-between;
  align-items: baseline;
  text-transform: uppercase;
  letter-spacing: 0.14em;
  font-family: 'IBM Plex Mono', monospace;
  font-size: 0.78rem;
  z-index: 1;
}

.signal-matrix__panel header span {
  color: rgba(146, 160, 196, 0.75);
}

.signal-matrix__panel h3 {
  font-size: 0.85rem;
}

.signal-matrix__sweep {
  position: relative;
  display: grid;
  gap: 1.1rem;
  z-index: 1;
}

.sweep__row {
  display: grid;
  gap: 0.55rem;
}

.sweep__meta {
  display: flex;
  justify-content: space-between;
  font-family: 'IBM Plex Mono', monospace;
  font-size: 0.68rem;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  color: rgba(146, 160, 196, 0.8);
}

.sweep__bar {
  position: relative;
  height: 6px;
  background: rgba(41, 240, 255, 0.14);
  overflow: hidden;
}

.sweep__bar span {
  position: absolute;
  inset: 0;
  background: linear-gradient(90deg, rgba(41, 240, 255, 0), rgba(41, 240, 255, 0.8));
  animation: sweep 4s linear infinite;
}

.sweep__value {
  font-family: 'IBM Plex Mono', monospace;
  font-size: 0.78rem;
  color: var(--accent-primary);
  letter-spacing: 0.1em;
  text-align: right;
}

.mesh__grid {
  display: grid;
  grid-template-columns: repeat(2, minmax(0, 1fr));
  gap: 1.4rem;
  z-index: 1;
}

.mesh__cell {
  position: relative;
  padding: 1.4rem 1.2rem;
  border: 1px solid rgba(41, 240, 255, 0.12);
  background: rgba(6, 10, 20, 0.78);
  display: grid;
  gap: 0.45rem;
  clip-path: polygon(0 0, 84% 0, 100% 26%, 100% 100%, 16% 100%, 0 74%);
  overflow: hidden;
}

.mesh__cell::before {
  content: '';
  position: absolute;
  inset: 0;
  background: linear-gradient(120deg, rgba(154, 92, 255, 0.18), transparent 60%);
  opacity: 0.7;
  mix-blend-mode: screen;
  pointer-events: none;
}

.mesh__label {
  font-family: 'IBM Plex Mono', monospace;
  text-transform: uppercase;
  letter-spacing: 0.16em;
  font-size: 0.65rem;
  color: rgba(146, 160, 196, 0.75);
}

.mesh__cell strong {
  font-size: 1.5rem;
  letter-spacing: 0.12em;
}

.mesh__meta {
  font-family: 'IBM Plex Mono', monospace;
  font-size: 0.7rem;
  color: var(--text-muted);
  letter-spacing: 0.08em;
}

.signal-matrix__panel--broadcast {
  padding-right: 3rem;
}

.broadcast__timeline {
  position: relative;
  display: grid;
  gap: 1.4rem;
  padding-left: 1.4rem;
  z-index: 1;
}

.broadcast__timeline::before {
  content: '';
  position: absolute;
  left: 0.2rem;
  top: 0.5rem;
  bottom: 0.5rem;
  background: linear-gradient(180deg, rgba(41, 240, 255, 0.4), rgba(154, 92, 255, 0.18));
  width: 1px;
}

.broadcast__pulse {
  display: flex;
  gap: 1rem;
  align-items: flex-start;
}

.broadcast__marker {
  position: relative;
  width: 0.9rem;
  height: 0.9rem;
  border-radius: 50%;
  background: radial-gradient(circle, rgba(92, 255, 196, 0.9), rgba(92, 255, 196, 0) 70%);
  box-shadow: 0 0 25px rgba(92, 255, 196, 0.6);
  animation: pulse 2.4s ease-in-out infinite;
}

.broadcast__body {
  display: grid;
  gap: 0.2rem;
  font-family: 'IBM Plex Mono', monospace;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  font-size: 0.7rem;
}

.broadcast__label {
  color: rgba(246, 247, 255, 0.85);
}

.broadcast__meta {
  color: rgba(146, 160, 196, 0.7);
}

.broadcast__value {
  color: var(--accent-primary);
}

@keyframes sweep {
  0% {
    transform: translateX(-60%);
  }
  100% {
    transform: translateX(0%);
  }
}

@keyframes pulse {
  0%,
  100% {
    transform: scale(1);
    opacity: 0.8;
  }
  50% {
    transform: scale(1.2);
    opacity: 1;
  }
}

@media (max-width: 1024px) {
  .signal-matrix__grid {
    grid-template-columns: repeat(2, minmax(0, 1fr));
  }
}

@media (max-width: 768px) {
  .signal-matrix__grid {
    grid-template-columns: 1fr;
  }

  .signal-matrix__panel {
    padding: 2rem;
  }

  .mesh__grid {
    grid-template-columns: repeat(auto-fit, minmax(160px, 1fr));
  }
}
</style>
