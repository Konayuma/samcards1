<template>
  <div class="ai-hub-wrapper">
    <!-- SVG Connections and Core -->
    <svg class="hub-svg" viewBox="0 0 800 600" xmlns="http://www.w3.org/2000/svg" preserveAspectRatio="xMidYMid meet">
      <defs>
        <linearGradient id="glowGradient" x1="0%" y1="0%" x2="100%" y2="100%">
          <stop offset="0%" stop-color="#00D2FF" />
          <stop offset="100%" stop-color="#3A7BD5" />
        </linearGradient>
        <filter id="neon-glow" x="-50%" y="-50%" width="200%" height="200%">
          <feGaussianBlur stdDeviation="6" result="blur1" />
          <feGaussianBlur stdDeviation="15" result="blur2" />
          <feMerge>
            <feMergeNode in="blur2" />
            <feMergeNode in="blur1" />
            <feMergeNode in="SourceGraphic" />
          </feMerge>
        </filter>
        <filter id="core-bloom" x="-100%" y="-100%" width="300%" height="300%">
          <feGaussianBlur stdDeviation="25" result="blur" />
          <feComposite in="SourceGraphic" in2="blur" operator="over" />
        </filter>
      </defs>

      <!-- Connection Lines (Nerves) -->
      <g stroke="#b0bec5" stroke-width="2" fill="none">
        <!-- Lines to cards -->
        <!-- Top Left -->
        <path d="M 400 300 C 300 300 250 150 150 150" :class="{ 'active-line': hoveredCard === 'tasks' }" />
        <path d="M 400 300 C 300 300 250 150 150 150" class="flow-line" :class="{ 'active-flow': hoveredCard === 'tasks' }" />
        
        <!-- Top Right -->
        <path d="M 400 300 C 500 300 550 150 650 150" :class="{ 'active-line': hoveredCard === 'analytics' }" />
        <path d="M 400 300 C 500 300 550 150 650 150" class="flow-line" :class="{ 'active-flow': hoveredCard === 'analytics' }" />

        <!-- Bottom Left -->
        <path d="M 400 300 C 300 300 250 450 150 450" :class="{ 'active-line': hoveredCard === 'workflows' }" />
        <path d="M 400 300 C 300 300 250 450 150 450" class="flow-line reverse" :class="{ 'active-flow': hoveredCard === 'workflows' }" />

        <!-- Bottom Right -->
        <path d="M 400 300 C 500 300 550 450 650 450" :class="{ 'active-line': hoveredCard === 'insights' }" />
        <path d="M 400 300 C 500 300 550 450 650 450" class="flow-line reverse" :class="{ 'active-flow': hoveredCard === 'insights' }" />
      </g>

      <!-- Core Sphere (AI Brain) -->
      <g transform="translate(400, 300)" class="core-group" filter="url(#core-bloom)">
        <!-- Ambient Base Glow -->
        <circle cx="0" cy="0" r="85" fill="url(#glowGradient)" opacity="0.15" class="core-pulse-base" />
        <circle cx="0" cy="0" r="65" fill="url(#glowGradient)" opacity="0.4" class="core-pulse-mid" />
        
        <!-- Plasma rings -->
        <g class="spin-slow">
          <ellipse cx="0" cy="0" rx="75" ry="25" fill="none" stroke="#00D2FF" stroke-width="2.5" transform="rotate(30)" opacity="0.8" filter="url(#neon-glow)" />
        </g>
        <g class="spin-fast">
          <ellipse cx="0" cy="0" rx="70" ry="15" fill="none" stroke="#ffffff" stroke-width="1.5" transform="rotate(-60)" opacity="0.9" filter="url(#neon-glow)" />
        </g>
        <g class="spin-medium">
          <ellipse cx="0" cy="0" rx="80" ry="30" fill="none" stroke="#3A7BD5" stroke-width="3" transform="rotate(80)" opacity="0.6" />
        </g>
        <g class="spin-alt">
          <ellipse cx="0" cy="0" rx="65" ry="65" fill="none" stroke="#00D2FF" stroke-width="0.5" transform="rotate(0)" opacity="0.5" stroke-dasharray="10 20"/>
        </g>

        <!-- Solid Inner Core -->
        <circle cx="0" cy="0" r="35" fill="#ffffff" filter="url(#neon-glow)" class="core-inner" />
      </g>
    </svg>

    <!-- HTML Glassmorphic Cards Overlay -->
    <div class="cards-overlay">
      <!-- Task Lists Card -->
      <div 
        class="glass-card card-tl" 
        @mouseenter="hoveredCard = 'tasks'" 
        @mouseleave="hoveredCard = null"
      >
        <h3>Task Lists</h3>
        <ul>
          <li><span class="icon-check">✔</span> Draft client proposal</li>
          <li><span class="icon-check">✔</span> Update analytics report</li>
          <li><span class="icon-check">✔</span> Schedule team sync</li>
        </ul>
      </div>

      <!-- Analytics Card -->
      <div 
        class="glass-card card-tr" 
        @mouseenter="hoveredCard = 'analytics'" 
        @mouseleave="hoveredCard = null"
      >
        <div class="card-header">
          <h3>Analytics</h3>
          <span class="badge positive">↑ 60% <span class="badge-sub">from last mth</span></span>
        </div>
        <div class="bar-chart">
          <div class="y-axis">
            <span>100%</span>
            <span>60%</span>
            <span>40%</span>
            <span>0%</span>
          </div>
          <div class="bars-container">
            <div class="bar-col">
              <div class="bar" style="height: 30%"></div>
              <span class="x-label">Apr</span>
            </div>
            <div class="bar-col">
              <div class="bar" style="height: 50%"></div>
              <span class="x-label">May</span>
            </div>
            <div class="bar-col">
              <div class="bar" style="height: 40%"></div>
              <span class="x-label">Jun</span>
            </div>
            <div class="bar-col">
              <div class="bar" style="height: 80%"></div>
              <span class="x-label">Jul</span>
            </div>
            <div class="bar-col">
              <div class="bar current" style="height: 100%"></div>
              <span class="x-label">Aug</span>
            </div>
          </div>
        </div>
      </div>

      <!-- Workflows Card -->
      <div 
        class="glass-card card-bl" 
        @mouseenter="hoveredCard = 'workflows'" 
        @mouseleave="hoveredCard = null"
      >
        <h3>Workflows</h3>
        <div class="workflow-steps">
          <div class="step">
            <span class="status-dot green"></span> Draft client proposal
          </div>
          <div class="connector-line"></div>
          <div class="step pending">
            <span class="status-dot yellow"></span> Manager review & approval
          </div>
          <div class="create-action">Create a workflow to publish a... <span class="cursor"></span></div>
        </div>
      </div>

      <!-- Insights Card -->
      <div 
        class="glass-card card-br" 
        @mouseenter="hoveredCard = 'insights'" 
        @mouseleave="hoveredCard = null"
      >
        <h3>Insights</h3>
        <div class="insight-box">
          <span class="icon"></span>
          <p class="insight-text">Automate your <strong>weekly reports</strong> slightly to save 4 hours/week.</p>
        </div>
        <div class="tags">
          <span class="tag"> Productivity trend</span>
          <span class="tag"> Focus on top</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const hoveredCard = ref(null)
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600&display=swap');

.ai-hub-wrapper {
  position: relative;
  width: 100%;
  max-width: 900px;
  min-height: 500px;
  aspect-ratio: 16/10;
  margin: 0 auto;
  font-family: 'Inter', sans-serif;
  color: #1e293b;
}

.hub-svg {
  width: 100%;
  height: 100%;
  position: absolute;
  top: 0;
  left: 0;
  z-index: 1;
}

/* Base Core Animations */
.spin-slow { animation: spin 20s linear infinite; transform-origin: 0 0; }
.spin-medium { animation: spin 15s linear infinite reverse; transform-origin: 0 0; }
.spin-fast { animation: spin 8s linear infinite; transform-origin: 0 0; }
.spin-alt { animation: spin 30s linear infinite; transform-origin: 0 0; }

@keyframes spin {
  100% { transform: rotate(360deg); }
}

.core-pulse-base { animation: pulseBase 4s ease-in-out infinite alternate; }
.core-pulse-mid { animation: pulseMid 3s ease-in-out infinite alternate; }
.core-inner { animation: pulseInner 2.5s ease-in-out infinite alternate; }

@keyframes pulseBase {
  0% { r: 80; opacity: 0.12; }
  100% { r: 92; opacity: 0.25; }
}
@keyframes pulseMid {
  0% { r: 58; opacity: 0.4; }
  100% { r: 68; opacity: 0.7; filter: drop-shadow(0 0 10px #00D2FF); }
}
@keyframes pulseInner {
  0% { r: 32; opacity: 0.8; filter: drop-shadow(0 0 15px #fff); }
  100% { r: 38; opacity: 1; filter: drop-shadow(0 0 25px #00D2FF); }
}

/* Nerves Data Flow Animations */
.flow-line {
  stroke: #00D2FF;
  stroke-width: 2.5;
  stroke-dasharray: 6 18;
  animation: flowForward 1.5s linear infinite;
  opacity: 0.2;
  filter: drop-shadow(0 0 3px #00D2FF);
  transition: all 0.4s ease;
}
.flow-line.reverse {
  animation: flowReverse 1.5s linear infinite;
}

.active-line {
  stroke: #3A7BD5;
  stroke-width: 3.5;
  transition: all 0.4s ease;
}
.active-flow {
  opacity: 0.9;
  stroke-width: 4;
  filter: drop-shadow(0 0 8px #00D2FF);
}

@keyframes flowForward {
  to { stroke-dashoffset: -24; }
}
@keyframes flowReverse {
  to { stroke-dashoffset: 24; }
}

/* Overlay & Glass Cards */
.cards-overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: 2;
  pointer-events: none; /* Allows interacting with lines underneath if needed */
}

.glass-card {
  position: absolute;
  pointer-events: auto;
  width: 240px;
  background: #ffffff;
  border: 1px solid #ebebeb;
  border-radius: 12px;
  padding: 1.25rem;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.05);
  transition: transform 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275), 
              box-shadow 0.4s ease, 
              border-color 0.4s ease;
  transform-origin: center;
}

.glass-card:hover {
  transform: scale(1.05) translateY(-5px);
  box-shadow: 0 6px 18px rgba(59, 130, 246, 0.1);
  border-color: #bfdbfe;
}

/* absolute positioning matching the SVG nerve endings */
.card-tl { top: 10%; left: 0%; }
.card-tr { top: 10%; right: 0%; }
.card-bl { bottom: 10%; left: 0%; }
.card-br { bottom: 10%; right: 0%; }

/* Card Interiors */
h3 {
  font-size: 0.95rem;
  font-weight: 600;
  margin: 0 0 0.8rem 0;
  color: #1e293b;
  letter-spacing: 0.3px;
}

/* TL: Task Lists */
.card-tl ul {
  list-style: none;
  padding: 0;
  margin: 0;
}
.card-tl li {
  font-size: 0.8rem;
  color: #475569;
  margin-bottom: 0.5rem;
  display: flex;
  align-items: center;
  gap: 0.5rem;
}
.icon-check {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  background: #00D2FF;
  color: #fff;
  border-radius: 50%;
  width: 14px;
  height: 14px;
  font-size: 0.55rem;
}

/* TR: Analytics */
.card-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 1rem;
}
.card-header h3 { margin: 0; }
.badge.positive {
  background: rgba(16, 185, 129, 0.15);
  color: #34d399;
  font-size: 0.7rem;
  padding: 0.2rem 0.5rem;
  border-radius: 6px;
  font-weight: 600;
  display: flex;
  align-items: center;
  gap: 0.3rem;
}
.badge-sub {
  color: #94a3b8;
  font-weight: 400;
  font-size: 0.6rem;
}
.bar-chart {
  display: flex;
  gap: 8px;
  height: 60px;
}
.y-axis {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  font-size: 0.55rem;
  color: #64748B;
  padding-right: 5px;
}
.bars-container {
  display: flex;
  flex: 1;
  justify-content: space-between;
  align-items: flex-end;
  height: 100%;
}
.bar-col {
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 15%;
  height: 100%;
  justify-content: flex-end;
  gap: 4px;
}
.bar {
  width: 100%;
  background: #dde3ec;
  border-radius: 3px 3px 0 0;
  transition: height 1s ease;
}
.bar.current {
  background: linear-gradient(to top, #3A7BD5, #00D2FF);
  box-shadow: 0 0 8px rgba(0, 210, 255, 0.5);
}
.x-label {
  font-size: 0.55rem;
  color: #64748B;
}

/* BL: Workflows */
.workflow-steps {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}
.step {
  font-size: 0.8rem;
  background: #e9edf3;
  border: 1px solid #d4dae4;
  padding: 0.5rem 0.75rem;
  border-radius: 6px;
  display: flex;
  align-items: center;
  gap: 0.5rem;
  color: #1e293b;
}
.step.pending {
  color: #64748b;
  opacity: 0.9;
}
.status-dot {
  width: 8px;
  height: 8px;
  border-radius: 50%;
}
.status-dot.green { background: #10B981; box-shadow: 0 0 5px #10B981; }
.status-dot.yellow { background: #F59E0B; }
.connector-line {
  width: 2px;
  height: 10px;
  background: #cbd5e1;
  margin-left: 1rem;
}
.create-action {
  font-size: 0.7rem;
  color: #64748b;
  margin-top: 0.5rem;
  display: flex;
  align-items: center;
  gap: 5px;
}
.cursor { font-size: 0.9rem; }

/* BR: Insights */
.insight-box {
  background: #edf0f5;
  padding: 0.75rem;
  border-radius: 8px;
  display: flex;
  gap: 0.5rem;
  margin-bottom: 0.75rem;
  border: 1px solid #d4dae4;
}
.insight-text {
  font-size: 0.75rem;
  color: #475569;
  line-height: 1.5;
  margin: 0;
}
.insight-text strong {
  color: #0f172a;
  font-weight: 600;
}
.tags {
  display: flex;
  gap: 0.5rem;
  flex-wrap: wrap;
}
.tag {
  font-size: 0.65rem;
  background: rgba(0, 210, 255, 0.1);
  color: #00D2FF;
  padding: 0.3rem 0.6rem;
  border-radius: 20px;
  border: 1px solid rgba(0, 210, 255, 0.2);
}

/* Responsive constraints */
@media (max-width: 992px) {
  .ai-hub-wrapper {
    aspect-ratio: auto;
    height: 600px;
    max-width: 600px;
  }
  .card-tl { top: 0; left: 0; transform: scale(0.9); }
  .card-tr { top: 0; right: 0; transform: scale(0.9); }
  .card-bl { bottom: 0; left: 0; transform: scale(0.9); }
  .card-br { bottom: 0; right: 0; transform: scale(0.9); }
  
  .glass-card:hover { transform: scale(0.95) translateY(-5px); }
}

@media (max-width: 768px) {
  .ai-hub-wrapper {
    height: auto;
    display: flex;
    flex-direction: column;
    gap: 1rem;
    align-items: center;
  }
  .hub-svg {
    position: relative;
    height: 300px;
  }
  .cards-overlay {
    position: relative;
    display: grid;
    grid-template-columns: 1fr;
    gap: 1rem;
  }
  .glass-card {
    position: relative;
    width: 100%;
    top: auto !important;
    left: auto !important;
    right: auto !important;
    bottom: auto !important;
    transform: none !important;
  }
}
</style>
