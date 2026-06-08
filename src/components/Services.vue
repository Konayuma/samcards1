<script setup>
import { ref } from 'vue'
import {
  AiLaptopIcon,
  Wrench01Icon,
  Idea01Icon,
  StudentIcon,
  JobSearchIcon,
  DeveloperIcon,
  MentoringIcon,
  UserGroupIcon,
  Presentation01Icon,
  QuillWrite01Icon,
  FlowSquareIcon,
  ChartIncreaseIcon,
  Mouse01Icon,
  AiPhone01Icon,
  Home01Icon,
  NewOfficeIcon,
  CodeIcon,
  AiNetworkIcon,
  AiSecurity01Icon
} from 'hugeicons-vue'

const activeTab = ref('services')

const services = ref([
  { id: 1,  title: 'IT Consultancy',                                              icon: AiLaptopIcon,       desc: 'Strategic technology advice to modernise your business.' },
  { id: 2,  title: 'Supply, Installation & Maintenance of IT Infrastructure',     icon: Wrench01Icon,       desc: 'End-to-end setup and upkeep of your IT systems.' },
  { id: 3,  title: 'Career Coaching',                                             icon: Idea01Icon,         desc: 'Personalised guidance to accelerate your career path.' },
  { id: 4,  title: 'Student Placement',                                           icon: StudentIcon,        desc: 'Connecting students with the right opportunities.' },
  { id: 5,  title: 'Recruitment & Talent Search',                                 icon: JobSearchIcon,      desc: 'Finding exceptional talent for your organisation.' },
  { id: 6,  title: 'Systems Development',                                         icon: DeveloperIcon,      desc: 'Custom software built to solve your unique challenges.' },
  { id: 7,  title: 'Student Mentorship',                                          icon: MentoringIcon,      desc: 'One-on-one mentorship to nurture the next generation.' },
  { id: 8,  title: 'Team Building',                                               icon: UserGroupIcon,      desc: 'Workshops and activities that forge high-performing teams.' },
  { id: 9,  title: 'Training',                                                    icon: Presentation01Icon, desc: 'Up-skill your workforce with hands-on training programmes.' },
  { id: 10, title: 'Content Creation & Management',                               icon: QuillWrite01Icon,   desc: 'Compelling content strategies that grow your brand.' },
  { id: 11, title: 'Process Analysis & Optimisation',                                icon: FlowSquareIcon,     desc: 'Mapping and streamlining your workflows to eliminate inefficiencies.' },
  { id: 12, title: 'Business Transformation & Change Management',                   icon: ChartIncreaseIcon,  desc: 'Guiding your organisation through structural and operational change.' },
])

const products = ref([
  { id: 1, title: 'High end and Gaming computers', icon: AiLaptopIcon, desc: 'Top-tier performance for gaming and professional workloads.' },
  { id: 2, title: 'Computer Accessories', icon: Mouse01Icon, desc: 'Essential peripherals to enhance your computing experience.' },
  { id: 3, title: 'Smart devices', icon: AiPhone01Icon, desc: 'Connected devices to keep you productive and in touch.' },
  { id: 4, title: 'Smart home devices', icon: Home01Icon, desc: 'Automate and secure your home with intelligent technology.' },
  { id: 5, title: 'Smart office devices', icon: NewOfficeIcon, desc: 'Modernise your workspace for maximum efficiency.' },
  { id: 6, title: 'Computer Software', icon: CodeIcon, desc: 'Essential software solutions for business and personal use.' },
  { id: 7, title: 'Networking equipment', icon: AiNetworkIcon, desc: 'Reliable networking gear to keep you connected.' },
  { id: 8, title: 'Security and surveillance', icon: AiSecurity01Icon, desc: 'Advanced systems to protect your premises and assets.' },
])
</script>

<template>
  <section class="services" id="services">
    <div class="container">
      <div class="section-header">
        <h2 class="section-title">Products & Services</h2>
        <div class="divider"></div>
        <p class="section-subtitle">Comprehensive solutions tailored to your business and personal growth needs.</p>
      </div>

      <div class="stepper-container">
        <button 
          class="stepper-btn" 
          :class="{ active: activeTab === 'services' }" 
          @click="activeTab = 'services'"
        >
          Services
        </button>
        <button 
          class="stepper-btn" 
          :class="{ active: activeTab === 'products' }" 
          @click="activeTab = 'products'"
        >
          Products
        </button>
      </div>
      
      <div v-if="activeTab === 'services'" class="services-grid">
        <div v-for="service in services" :key="service.id" class="service-card">
          <div class="card-inner">
            <div class="service-icon-wrap">
              <component :is="service.icon" class="service-icon" size="36" />
            </div>
            <h3 class="service-title">{{ service.title }}</h3>
            <p class="service-desc">{{ service.desc }}</p>
            <div class="card-arrow">→</div>
          </div>
        </div>
      </div>

      <div v-if="activeTab === 'products'" class="services-grid">
        <div v-for="product in products" :key="product.id" class="service-card">
          <div class="card-inner">
            <div class="service-icon-wrap">
              <component :is="product.icon" class="service-icon" size="36" />
            </div>
            <h3 class="service-title">{{ product.title }}</h3>
            <p class="service-desc">{{ product.desc }}</p>
            <div class="card-arrow">→</div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.services {
  padding: 6rem 0;
  background: linear-gradient(160deg, #f4f6f9 0%, #eef1f7 100%);
}

.section-header {
  text-align: center;
  margin-bottom: 4rem;
}

.section-title {
  font-size: 2.5rem;
  color: var(--dark-text);
  margin-bottom: 1rem;
  font-weight: 800;
}

.divider {
  height: 4px;
  width: 60px;
  background: linear-gradient(90deg, var(--primary-blue), #a8c8f0);
  margin: 0 auto 1.5rem auto;
  border-radius: 2px;
}

.section-subtitle {
  font-size: 1.15rem;
  color: #666;
  max-width: 600px;
  margin: 0 auto;
}

/* Stepper */
.stepper-container {
  display: flex;
  justify-content: center;
  gap: 1rem;
  margin-bottom: 3rem;
}

.stepper-btn {
  background: white;
  border: 2px solid transparent;
  padding: 0.75rem 2rem;
  font-size: 1.1rem;
  font-weight: 600;
  color: #666;
  border-radius: 30px;
  cursor: pointer;
  transition: all 0.3s ease;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.05);
}

.stepper-btn:hover {
  color: var(--primary-blue);
  transform: translateY(-2px);
}

.stepper-btn.active {
  background: var(--primary-blue);
  color: white;
  box-shadow: 0 8px 20px rgba(91, 155, 213, 0.3);
}

/* Grid */
.services-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
  gap: 1.75rem;
}

/* Card */
.service-card {
  background: white;
  border-radius: 16px;
  overflow: hidden;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.06);
  transition: transform 0.35s cubic-bezier(0.34, 1.56, 0.64, 1),
              box-shadow 0.35s ease;
  cursor: default;
}

.service-card:hover {
  transform: translateY(-8px) scale(1.02);
  box-shadow: 0 20px 40px rgba(91, 155, 213, 0.2);
}

.card-inner {
  padding: 2rem 1.75rem;
  position: relative;
  display: flex;
  flex-direction: column;
  gap: 0.75rem;
  height: 100%;
  border-top: 3px solid transparent;
  transition: border-color 0.3s ease;
  border-radius: 16px;
}

/* Icon bubble */
.service-icon-wrap {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  width: 64px;
  height: 64px;
  border-radius: 16px;
  background: #eef4fb;
  color: var(--primary-blue);
  transition: background 0.3s ease, transform 0.3s ease;
  flex-shrink: 0;
}

.service-card:hover .service-icon-wrap {
  background: var(--primary-blue);
  color: white;
  transform: rotate(-6deg) scale(1.1);
}

.service-icon {
  display: block;
}

/* Text */
.service-title {
  font-size: 1.05rem;
  font-weight: 700;
  color: var(--dark-text);
  line-height: 1.3;
  margin: 0;
}

.service-desc {
  font-size: 0.92rem;
  color: #777;
  line-height: 1.6;
  margin: 0;
  flex: 1;
}

/* Arrow */
.card-arrow {
  font-size: 1.1rem;
  color: var(--primary-blue);
  font-weight: 700;
  opacity: 0;
  transform: translateX(-6px);
  transition: opacity 0.3s ease, transform 0.3s ease;
  align-self: flex-end;
}

.service-card:hover .card-arrow {
  opacity: 1;
  transform: translateX(0);
}

@media (max-width: 768px) {
  .services-grid {
    grid-template-columns: 1fr;
  }
}
</style>