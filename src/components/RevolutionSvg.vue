<template>
  <div class="svg-container">
    <svg viewBox="0 0 500 500" xmlns="http://www.w3.org/2000/svg" class="revolution-svg">
      <defs>
        <!-- Gradients -->
        <linearGradient id="grad1" x1="0%" y1="0%" x2="100%" y2="100%">
          <stop offset="0%" stop-color="#2a75d3" stop-opacity="0.8" />
          <stop offset="100%" stop-color="#1542a3" stop-opacity="1" />
        </linearGradient>
        <linearGradient id="grad2" x1="100%" y1="0%" x2="0%" y2="100%">
          <stop offset="0%" stop-color="#00d2ff" stop-opacity="0.8" />
          <stop offset="100%" stop-color="#3a7bd5" stop-opacity="1" />
        </linearGradient>
        <linearGradient id="orbitGrad" x1="0%" y1="0%" x2="100%" y2="100%">
          <stop offset="0%" stop-color="#2a75d3" stop-opacity="0.1" />
          <stop offset="50%" stop-color="#2a75d3" stop-opacity="0.6" />
          <stop offset="100%" stop-color="#2a75d3" stop-opacity="0.1" />
        </linearGradient>
        
        <!-- Glow effect -->
        <filter id="glow" x="-20%" y="-20%" width="140%" height="140%">
          <feGaussianBlur stdDeviation="8" result="blur" />
          <feComposite in="SourceGraphic" in2="blur" operator="over" />
        </filter>
      </defs>

      <!-- Center Node (Core Business) -->
      <g class="core" filter="url(#glow)">
        <circle cx="250" cy="250" r="45" fill="url(#grad1)" />
        <circle cx="250" cy="250" r="30" fill="#ffffff" opacity="0.1" />
        <!-- Data lines emitted from center -->
        <path d="M250,210 L250,180" stroke="#fff" stroke-width="3" stroke-linecap="round" class="pulse-line" />
        <path d="M250,290 L250,320" stroke="#fff" stroke-width="3" stroke-linecap="round" class="pulse-line" />
        <path d="M210,250 L180,250" stroke="#fff" stroke-width="3" stroke-linecap="round" class="pulse-line" />
        <path d="M290,250 L320,250" stroke="#fff" stroke-width="3" stroke-linecap="round" class="pulse-line" />
      </g>

      <!-- Inner Orbit -->
      <g class="orbit-group-1">
        <circle cx="250" cy="250" r="100" fill="none" stroke="url(#orbitGrad)" stroke-width="2" stroke-dasharray="8,6" />
        <!-- Orbiting Nodes -->
        <circle cx="250" cy="150" r="15" fill="url(#grad2)" />
        <circle cx="250" cy="350" r="15" fill="url(#grad2)" />
        <circle cx="150" cy="250" r="15" fill="url(#grad2)" />
        <circle cx="350" cy="250" r="15" fill="url(#grad2)" />
        <animateTransform 
          attributeName="transform"
          type="rotate"
          from="0 250 250"
          to="360 250 250"
          dur="15s"
          repeatCount="indefinite"
        />
      </g>

      <!-- Outer Orbit -->
      <g class="orbit-group-2">
        <circle cx="250" cy="250" r="180" fill="none" stroke="url(#orbitGrad)" stroke-width="1.5" stroke-dasharray="10,12" />
        <!-- Satellites -->
        <g transform="translate(250, 70)">
          <circle cx="0" cy="0" r="10" fill="#2a75d3" />
          <circle cx="0" cy="0" r="20" fill="none" stroke="#2a75d3" stroke-width="1" class="ripple" />
        </g>
        <g transform="translate(250, 430)">
          <circle cx="0" cy="0" r="10" fill="#2a75d3" />
          <circle cx="0" cy="0" r="20" fill="none" stroke="#2a75d3" stroke-width="1" class="ripple" />
        </g>
        <g transform="translate(70, 250)">
          <circle cx="0" cy="0" r="10" fill="#2a75d3" />
          <circle cx="0" cy="0" r="20" fill="none" stroke="#2a75d3" stroke-width="1" class="ripple" />
        </g>
        <g transform="translate(430, 250)">
          <circle cx="0" cy="0" r="10" fill="#2a75d3" />
          <circle cx="0" cy="0" r="20" fill="none" stroke="#2a75d3" stroke-width="1" class="ripple" />
        </g>
        <!-- Rotation -->
        <animateTransform 
          attributeName="transform"
          type="rotate"
          from="360 250 250"
          to="0 250 250"
          dur="25s"
          repeatCount="indefinite"
        />
      </g>
      
      <!-- Connective sweeping radar / tech lines -->
      <path d="M250,250 L430,250" stroke="url(#grad2)" stroke-width="2" opacity="0.4">
        <animateTransform 
          attributeName="transform"
          type="rotate"
          from="0 250 250"
          to="360 250 250"
          dur="5s"
          repeatCount="indefinite"
        />
      </path>
    </svg>
  </div>
</template>

<style scoped>
.svg-container {
  width: 100%;
  max-width: 500px;
  height: auto;
  display: flex;
  justify-content: center;
  align-items: center;
}

.revolution-svg {
  width: 100%;
  height: 100%;
  drop-shadow: 0px 10px 20px rgba(42, 117, 211, 0.2);
}

.core {
  animation: corePulse 3s infinite alternate ease-in-out;
  transform-origin: center;
}

@keyframes corePulse {
  0% { transform: scale(0.95); opacity: 0.9; }
  100% { transform: scale(1.05); opacity: 1; }
}

.pulse-line {
  stroke-dasharray: 40;
  stroke-dashoffset: 40;
  animation: drawLine 2s infinite ease-out;
}

@keyframes drawLine {
  0% { stroke-dashoffset: 40; opacity: 1; }
  50% { stroke-dashoffset: 0; opacity: 1; }
  100% { stroke-dashoffset: -40; opacity: 0; }
}

.ripple {
  animation: rippleEffect 2s infinite ease-out;
  transform-origin: center;
}

@keyframes rippleEffect {
  0% { transform: scale(0.5); opacity: 1; }
  100% { transform: scale(1.8); opacity: 0; }
}
</style>
