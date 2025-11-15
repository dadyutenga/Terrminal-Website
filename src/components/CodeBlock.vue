<template>
  <pre class="code-block">
    <code>
      <span v-for="(line, index) in renderedLines" :key="index" class="code-block__line">
        <span class="code-block__index">{{ index + 1 }}</span>
        <span class="code-block__content" v-html="highlight(line)"></span>
      </span>
    </code>
  </pre>
</template>

<script setup>
import { computed } from 'vue';

const props = defineProps({
  lines: {
    type: Array,
    default: () => []
  }
});

const renderedLines = computed(() => props.lines);

const highlight = (line) => {
  return line
    .replace(/module|service|gateway|pipeline/g, '<span class="token-keyword">$&</span>')
    .replace(/\b(listen|dispatch|spin|enforce|sandbox|audit|schedule|route)\b/g, '<span class="token-fn">$&</span>')
    .replace(/\"([^\"]+)\"/g, '<span class="token-string">"$1"</span>')
    .replace(/\b([0-9]+ms|[0-9]+)\b/g, '<span class="token-number">$1</span>')
    .replace(/stdin|cognition|plugins|docker|cron|mesh|telemetry/g, '<span class="token-identifier">$&</span>');
};
</script>

<style scoped>
.code-block {
  position: relative;
  padding: 2.5rem 2rem;
  margin: 0;
  background: rgba(8, 10, 22, 0.88);
  border: 1px solid rgba(41, 240, 255, 0.18);
  clip-path: polygon(0 0, 88% 0, 100% 18%, 100% 100%, 10% 100%, 0 82%);
  overflow: auto;
}

.code-block code {
  font-family: 'IBM Plex Mono', monospace;
  font-size: 0.95rem;
  letter-spacing: 0.04em;
  color: var(--text-primary);
  display: grid;
  gap: 0.4rem;
}

.code-block__line {
  display: grid;
  grid-template-columns: 2.8rem 1fr;
  gap: 1.5rem;
  align-items: start;
}

.code-block__index {
  color: rgba(146, 160, 196, 0.5);
  text-align: right;
}

.token-keyword {
  color: var(--accent-secondary);
}

.token-fn {
  color: var(--accent-primary);
}

.token-string {
  color: rgba(92, 255, 196, 0.9);
}

.token-number {
  color: rgba(255, 196, 92, 0.9);
}

.token-identifier {
  color: rgba(41, 240, 255, 0.8);
}

@media (max-width: 640px) {
  .code-block {
    padding: 2rem 1.5rem;
  }

  .code-block__line {
    grid-template-columns: 2rem 1fr;
  }
}
</style>
