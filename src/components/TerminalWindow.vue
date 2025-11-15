<template>
  <div class="terminal" @mousedown="startDrag" @touchstart.prevent="startDrag">
    <div class="terminal__chrome">
      <div class="terminal__lights">
        <span></span>
        <span></span>
        <span></span>
      </div>
      <p>demo@terminal-agent:~</p>
      <div class="terminal__status">LIVE</div>
    </div>
    <div class="terminal__body" ref="body">
      <TransitionGroup name="line" tag="div" class="terminal__lines">
        <div v-for="line in visibleLines" :key="line.id" class="terminal__line">
          <span class="terminal__prompt" v-if="line.prompt">{{ line.prompt }}</span>
          <span class="terminal__text" v-html="line.text"></span>
        </div>
      </TransitionGroup>
    </div>
  </div>
</template>

<script setup>
import { onMounted, onUnmounted, reactive, ref } from 'vue';

const body = ref(null);
const visibleLines = reactive([]);
let pointerOffset = { x: 0, y: 0 };
let isDragging = false;
const steps = [
  { prompt: 'user@station', text: ' execute pipeline deploy --target=staging' },
  { prompt: 'agent@hypervisor', text: ' Validating manifests... <span class="text-muted">OK</span>' },
  { prompt: 'agent@hypervisor', text: ' Spinning up containers: <span class="text-accent">8 online</span>' },
  {
    prompt: 'agent@hypervisor',
    text: ' Telemetry ↯ latency=11.8ms | throughput=4.2gbps'
  },
  {
    prompt: 'agent@hypervisor',
    text: ' Deploy complete. <span class="text-success">All systems synced.</span>'
  },
  {
    prompt: 'user@station',
    text: ' query metrics --window=5m --agg=latency'
  },
  {
    prompt: 'agent@hypervisor',
    text: ' Median latency: <span class="text-accent">11.3ms</span> | p99: <span class="text-muted">18.6ms</span>'
  }
];
let lineTimer;
let counter = 0;

const pushLine = () => {
  if (counter >= steps.length) {
    counter = 0;
    visibleLines.splice(0, visibleLines.length);
  }
  const next = steps[counter];
  visibleLines.push({ ...next, id: `${Date.now()}-${counter}` });
  counter += 1;
  if (visibleLines.length > 5) {
    visibleLines.shift();
  }
};

const loopLines = () => {
  pushLine();
  lineTimer = setInterval(pushLine, 2200);
};

const startDrag = (event) => {
  isDragging = true;
  const { clientX, clientY } = 'touches' in event ? event.touches[0] : event;
  const rect = event.currentTarget.getBoundingClientRect();
  pointerOffset = { x: clientX - rect.left, y: clientY - rect.top };
  window.addEventListener('mousemove', moveDrag);
  window.addEventListener('mouseup', endDrag);
  window.addEventListener('touchmove', moveDrag, { passive: false });
  window.addEventListener('touchend', endDrag);
};

const moveDrag = (event) => {
  if (!isDragging) return;
  const { clientX, clientY } = 'touches' in event ? event.touches[0] : event;
  const element = body.value?.parentElement;
  if (!element) return;
  element.style.transform = `translate(${clientX - pointerOffset.x}px, ${clientY - pointerOffset.y}px)`;
};

const endDrag = () => {
  isDragging = false;
  window.removeEventListener('mousemove', moveDrag);
  window.removeEventListener('mouseup', endDrag);
  window.removeEventListener('touchmove', moveDrag);
  window.removeEventListener('touchend', endDrag);
};

onMounted(() => {
  loopLines();
});

onUnmounted(() => {
  clearInterval(lineTimer);
  endDrag();
});
</script>

<style scoped>
.terminal {
  position: relative;
  background: linear-gradient(160deg, rgba(12, 16, 32, 0.9), rgba(6, 8, 18, 0.9));
  border: 1px solid rgba(41, 240, 255, 0.16);
  clip-path: polygon(0 0, 90% 0, 100% 12%, 100% 100%, 10% 100%, 0 88%);
  box-shadow: 0 30px 60px rgba(0, 0, 0, 0.55);
  cursor: grab;
  transition: box-shadow 0.4s ease;
  will-change: transform;
}

.terminal:active {
  cursor: grabbing;
}

.terminal__chrome {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 1rem 1.5rem;
  border-bottom: 1px solid rgba(41, 240, 255, 0.12);
  font-family: 'IBM Plex Mono', monospace;
  text-transform: uppercase;
  letter-spacing: 0.2em;
  font-size: 0.72rem;
  background: rgba(9, 12, 24, 0.85);
}

.terminal__lights {
  display: flex;
  gap: 0.4rem;
}

.terminal__lights span {
  width: 0.6rem;
  height: 0.6rem;
  border-radius: 50%;
  background: linear-gradient(145deg, rgba(41, 240, 255, 0.9), rgba(41, 240, 255, 0.3));
  opacity: 0.65;
}

.terminal__status {
  color: var(--accent-primary);
}

.terminal__body {
  padding: 1.5rem 2rem;
  min-height: 280px;
  font-family: 'IBM Plex Mono', monospace;
  font-size: 0.95rem;
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.terminal__lines {
  display: flex;
  flex-direction: column;
  gap: 0.75rem;
}

.terminal__line {
  display: flex;
  gap: 0.8rem;
}

.terminal__prompt {
  color: var(--accent-secondary);
}

.terminal__text {
  color: var(--text-primary);
}

.text-muted {
  color: rgba(146, 160, 196, 0.7);
}

.text-success {
  color: rgba(92, 255, 196, 0.95);
}

.text-accent {
  color: var(--accent-primary);
}

.line-enter-active,
.line-leave-active {
  transition: all 0.4s ease;
}

.line-enter-from {
  opacity: 0;
  transform: translateY(12px);
}

.line-leave-to {
  opacity: 0;
  transform: translateY(-12px);
}

@media (max-width: 640px) {
  .terminal {
    clip-path: polygon(0 0, 88% 0, 100% 14%, 100% 100%, 12% 100%, 0 86%);
  }

  .terminal__body {
    padding: 1.25rem 1.6rem;
    min-height: 240px;
  }
}
</style>
