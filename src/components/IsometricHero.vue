<template>
  <div class="isometric-hero-container">
    <svg viewBox="0 0 800 600" xmlns="http://www.w3.org/2000/svg" class="isometric-svg">
      <defs>
        <!-- Gradients for the Core Processor -->
        <linearGradient id="coreGlow" x1="0%" y1="0%" x2="100%" y2="100%">
          <stop offset="0%" stop-color="#EFF6FF" />
          <stop offset="100%" stop-color="#93C5FD" />
        </linearGradient>
        
        <!-- Drop shadow and blur filters to create depth & glow effects -->
        <filter id="glow" x="-50%" y="-50%" width="200%" height="200%">
          <feGaussianBlur stdDeviation="15" result="blur" />
          <feComposite in="SourceGraphic" in2="blur" operator="over" />
        </filter>
        <filter id="core-glow" x="-50%" y="-50%" width="200%" height="200%">
          <feGaussianBlur stdDeviation="20" result="blur" />
          <feComposite in="SourceGraphic" in2="blur" operator="over" />
        </filter>
        <filter id="shadow" x="-20%" y="-20%" width="140%" height="140%">
          <feDropShadow dx="0" dy="25" stdDeviation="20" flood-color="#1E3A8A" flood-opacity="0.15" />
        </filter>
        <filter id="block-shadow" x="-50%" y="-50%" width="200%" height="200%">
          <feDropShadow dx="0" dy="15" stdDeviation="10" flood-color="#1E3A8A" flood-opacity="0.25" />
        </filter>

        <!-- Reusable Component Blocks (Isometric Projections) -->
        
        <!-- Standard Data Block -->
        <g id="data-block">
          <!-- Top Face -->
          <polygon points="0,0 20,-10 40,0 20,10" fill="#60A5FA" />
          <!-- Left Face -->
          <polygon points="0,0 20,10 20,30 0,20" fill="#3B82F6" />
          <!-- Right Face -->
          <polygon points="40,0 20,10 20,30 40,20" fill="#1D4ED8" />
        </g>

        <!-- Central Processor Core -->
        <g id="core-block">
          <!-- Top Face -->
          <polygon points="0,0 60,-30 120,0 60,30" fill="url(#coreGlow)" />
          <!-- Left Face -->
          <polygon points="0,0 60,30 60,90 0,60" fill="#3B82F6" />
          <!-- Right Face -->
          <polygon points="120,0 60,30 60,90 120,60" fill="#1E3A8A" />
          
          <!-- Inner glowing core -->
          <polygon points="20,0 60,-20 100,0 60,20" fill="#FFFFFF" opacity="0.9" filter="url(#core-glow)"/>
        </g>

        <!-- Main Base Platform -->
        <g id="base-plate">
          <!-- Surface -->
          <polygon points="0,0 250,-125 500,0 250,125" fill="#F8FAFC" stroke="#E2E8F0" stroke-width="2" />
          <!-- Left Depth -->
          <polygon points="0,0 250,125 250,145 0,20" fill="#E2E8F0" />
          <!-- Right Depth -->
          <polygon points="500,0 250,125 250,145 500,20" fill="#CBD5E1" />
          
          <!-- Grid lines aligned to isometric axes -->
          <g stroke="#E2E8F0" stroke-width="1.5">
            <path d="M 50,-25 L 300,100 M 100,-50 L 350,75 M 150,-75 L 400,50 M 200,-100 L 450,25" />
            <path d="M 50,25 L 300,-100 M 100,50 L 350,-75 M 150,75 L 400,-50 M 200,100 L 450,-25" />
          </g>
        </g>

        <!-- Small Platform -->
        <g id="base-plate-small">
          <polygon points="0,0 80,-40 160,0 80,40" fill="#F1F5F9" />
          <polygon points="0,0 80,40 80,55 0,15" fill="#E2E8F0" />
          <polygon points="160,0 80,40 80,55 160,15" fill="#CBD5E1" />
        </g>
      </defs>

      <!-- Global Assembly Structure -->
      <!-- Translate places the origin (0,0) so the model centers within the viewBox -->
      <g class="assembly" transform="translate(150, 300)">
        
        <!-- 1. The main foundation platform -->
        <g transform="translate(0, 50)" filter="url(#shadow)">
          <use href="#base-plate" />
        </g>

        <!-- 2. Integrated Workflows / Paths -->
        <g class="workflows" transform="translate(0, 50)">
          <!-- Connects left secondary hub to central processor base -->
          <path d="M 60,-10 L 170,45 L 250,5" fill="none" class="wire" />
          <path d="M 60,-10 L 170,45 L 250,5" fill="none" class="wire-flow flow-1" />
          
          <!-- Connects bottom right to central processor base -->
          <path d="M 400,-10 L 330,25 L 250,5" fill="none" class="wire" />
          <path d="M 400,-10 L 330,25 L 250,5" fill="none" class="wire-flow flow-2" />
          
          <!-- Connects top right to central processor base -->
          <path d="M 330,-115 L 250,-75 L 250,5" fill="none" class="wire" />
          <path d="M 330,-115 L 250,-75 L 250,5" fill="none" class="wire-flow flow-3" />
        </g>

        <!-- 3. Dynamic Data Stream Blocks - Moving along workflow paths -->
        <g class="data-stream stream-1">
          <g transform="translate(-10, -5) scale(0.5)">
            <use href="#data-block" />
          </g>
        </g>
        <g class="data-stream stream-2">
          <g transform="translate(-10, -5) scale(0.5)">
            <use href="#data-block" />
          </g>
        </g>
        <g class="data-stream stream-3">
          <g transform="translate(-10, -5) scale(0.5)">
            <use href="#data-block" />
          </g>
        </g>

        <!-- 4. Modular Secondary Processing Hubs (Floating independently) -->
        <!-- Left Processing Hub -->
        <g transform="translate(-20, 20)">
          <use href="#base-plate-small" />
          <g class="float-slow" transform="translate(60, -25)" filter="url(#block-shadow)">
            <use href="#data-block" />
          </g>
        </g>
        
        <!-- Bottom Right Processing Hub -->
        <g transform="translate(320, 20)">
          <use href="#base-plate-small" />
          <g class="float-med" transform="translate(40, -40)" filter="url(#block-shadow)">
            <use href="#data-block" transform="scale(0.8)" />
          </g>
          <g class="float-fast" transform="translate(80, -20)" filter="url(#block-shadow)">
            <use href="#data-block" />
          </g>
        </g>

        <!-- Top Right Processing Hub -->
        <g transform="translate(250, -85)">
          <use href="#base-plate-small" transform="scale(0.8)" />
          <g class="float-med" transform="translate(45, -20)" filter="url(#block-shadow)">
            <use href="#data-block" transform="scale(0.6)" />
          </g>
        </g>

        <!-- 5. Central Core Processor (Pulsing and Floating) -->
        <g transform="translate(190, -10)" class="core-float">
          <!-- Platform under core -->
          <polygon points="10,0 60,-25 110,0 60,25" fill="#DBEAFE" />
          
          <!-- The Glowing Pulse Core -->
          <g transform="translate(0, -45)" class="core-pulse">
            <use href="#core-block" />
          </g>
          
          <!-- Upward Energy / Data Beams emitted from core -->
          <g transform="translate(60, -45)">
            <path d="M 0,-30 L 0,-180" class="beam" />
            <path d="M -20,-15 L -20,-120" class="beam beam-alt" />
            <path d="M 20,-15 L 20,-140" class="beam beam-alt2" />
          </g>
        </g>

      </g>
    </svg>
  </div>
</template>

<style scoped>
.isometric-hero-container {
  width: 100%;
  max-width: 800px;
  height: 100%;
  min-height: 400px;
  display: flex;
  justify-content: center;
  align-items: center;
  /* Optional: a subtle radial background gradient to make the whites pop could be placed around this container */
}

.isometric-svg {
  width: 100%;
  height: auto;
  overflow: visible;
  filter: drop-shadow(0 20px 40px rgba(30, 58, 138, 0.05));
}

/* 1. Global Assembly Floating (Gentle vertical hover) */
.assembly {
  animation: floatAssembly 8s ease-in-out infinite;
  transform-origin: center;
}

@keyframes floatAssembly {
  0%, 100% { transform: translate(150px, 280px); }
  50% { transform: translate(150px, 270px); }
}

/* 2. Workflow Wiring & Pulsing Lines */
.wire {
  stroke: #DBEAFE;
  stroke-width: 4;
  stroke-linecap: round;
  stroke-linejoin: round;
}

.wire-flow {
  stroke: #3B82F6;
  stroke-width: 4;
  stroke-linecap: round;
  stroke-linejoin: round;
  stroke-dasharray: 12 24;
  animation: flowWire 1.5s linear infinite;
  opacity: 0.9;
  filter: drop-shadow(0 0 6px #60A5FA);
}

.flow-1 { animation-direction: normal; animation-duration: 2s; }
.flow-2 { animation-direction: reverse; animation-duration: 1.5s; stroke-dasharray: 8 16; }
.flow-3 { animation-direction: normal; stroke-dasharray: 10 20; animation-duration: 1.8s; }

@keyframes flowWire {
  from { stroke-dashoffset: 36; }
  to { stroke-dashoffset: 0; }
}

/* 3. Floating Data Blocks (Independent timing to simulate varying processing loads) */
.float-slow { animation: floatBlock 5s ease-in-out infinite 0.5s; }
.float-med { animation: floatBlock 3.5s ease-in-out infinite 1s; }
.float-fast { animation: floatBlock 2.5s ease-in-out infinite 0s; }

@keyframes floatBlock {
  0%, 100% { transform: translateY(0); }
  50% { transform: translateY(-15px); }
}

/* 4. Central Core Assembly Animation */
.core-float {
  animation: floatCore 6s ease-in-out infinite 1.5s;
}

@keyframes floatCore {
  0%, 100% { transform: translate(190px, -10px); }
  50% { transform: translate(190px, -20px); }
}

/* Core pulsating breathing effect applied to shadows / opacity */
.core-pulse {
  animation: coreGlow 3s ease-in-out infinite alternate;
}

@keyframes coreGlow {
  0% { 
    filter: drop-shadow(0 0 10px rgba(59, 130, 246, 0.4)) drop-shadow(0 15px 15px rgba(30, 58, 138, 0.3)); 
    opacity: 0.95; 
  }
  100% { 
    filter: drop-shadow(0 0 35px rgba(59, 130, 246, 0.9)) drop-shadow(0 25px 20px rgba(30, 58, 138, 0.2)); 
    opacity: 1; 
  }
}

/* 5. Emitting Energy Beams (Upward flow) */
.beam {
  stroke: #60A5FA;
  stroke-width: 2.5;
  stroke-dasharray: 20 15;
  animation: beamRise 1.2s linear infinite;
  stroke-linecap: round;
  opacity: 0.8;
  filter: drop-shadow(0 0 4px #3B82F6);
}

.beam-alt { 
  stroke: #93C5FD; 
  stroke-width: 1.5; 
  animation-duration: 0.9s; 
  opacity: 0.6; 
  stroke-dasharray: 12 18; 
}

.beam-alt2 { 
  stroke: #BFDBFE; 
  stroke-width: 2; 
  animation-duration: 1.5s; 
  opacity: 0.7; 
  stroke-dasharray: 25 25; 
}

@keyframes beamRise {
  from { stroke-dashoffset: 0; }
  to { stroke-dashoffset: -35; } /* Same sign as movement visually */
}

/* 6. Dynamic Data Conveyor Belt - Moving elements precisely along the paths matching XYZ isometric dimensions */

/* Path 1: 60,-10 → 170,45 → 250,5 */
.stream-1 {
  animation: drivePath1 4s linear infinite;
  /* Apply path coordinates offset */
}
@keyframes drivePath1 {
  0% { transform: translate(60px, 40px); opacity: 0; }
  5% { opacity: 1; }
  45% { transform: translate(170px, 95px); }
  90% { transform: translate(250px, 55px); opacity: 1; }
  100% { transform: translate(250px, 55px); opacity: 0; }
}

/* Path 2: 400,-10 → 330,25 → 250,5 */
.stream-2 {
  animation: drivePath2 4.5s linear infinite 1.5s;
  opacity: 0;
}
@keyframes drivePath2 {
  0% { transform: translate(400px, 40px); opacity: 0; }
  5% { opacity: 1; }
  45% { transform: translate(330px, 75px); }
  90% { transform: translate(250px, 55px); opacity: 1; }
  100% { transform: translate(250px, 55px); opacity: 0; }
}

/* Path 3: 330,-115 → 250,-75 → 250,5 */
.stream-3 {
  animation: drivePath3 3.8s linear infinite 0.8s;
  opacity: 0;
}
@keyframes drivePath3 {
  0% { transform: translate(330px, -65px); opacity: 0; }
  5% { opacity: 1; }
  45% { transform: translate(250px, -25px); }
  90% { transform: translate(250px, 55px); opacity: 1; }
  100% { transform: translate(250px, 55px); opacity: 0; }
}
</style>
