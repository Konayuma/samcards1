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
} from 'hugeicons-vue'

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
])
</script>

<template>
  <section class="services" id="services">
    <div class="container">
      <div class="section-header">
        <h2 class="section-title">Our Services</h2>
        <div class="divider"></div>
        <p class="section-subtitle">Comprehensive solutions tailored to your business and personal growth needs.</p>
      </div>
      
      <div class="services-grid">
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

.service-card:hover .card-inner {
  border-top-color: var(--primary-blue);
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