<template>
  <section id="experience">
    <div class="container">
      <div class="section-title">
        <div class="accent-line"></div>
        <h2>Expériences</h2>
        <p>Cliquez pour voir les détails</p>
      </div>

      <div class="exp-list">
        <div
          v-for="(exp, i) in experiences"
          :key="i"
          class="exp-item"
          :class="{ open: openIndex === i }"
        >
          <!-- Header (clickable) -->
          <button class="exp-header" @click="toggle(i)">
            <div class="exp-header-left">
              <span class="exp-dot" :style="{ background: exp.dotColor }"></span>
              <div>
                <h3>{{ exp.title }}</h3>
                <span class="exp-meta">{{ exp.type }} · {{ exp.date }}</span>
              </div>
            </div>
            <i class="fas fa-chevron-down exp-chevron"></i>
          </button>

          <!-- Details (toggle) -->
          <div class="exp-details" v-show="openIndex === i">
            <p class="exp-company" v-if="exp.company">
              <i class="fas fa-building"></i> {{ exp.company }}
            </p>
            <ul class="exp-points">
              <li v-for="(point, j) in exp.highlights" :key="j">{{ point }}</li>
            </ul>
            <div class="exp-tags">
              <span v-for="tag in exp.tags" :key="tag" class="badge badge-dark">{{ tag }}</span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue'

const openIndex = ref(null)

const toggle = (i) => {
  openIndex.value = openIndex.value === i ? null : i
}

const experiences = [
  {
    title: 'Site de suivi de colis',
    type: 'Freelance',
    date: 'Fév. 2026',
    company: null,
    dotColor: 'var(--red)',
    highlights: [
      'Application web de suivi de colis en temps réel (Laravel, MySQL, Tailwind CSS).',
      'Tableau de bord admin avec CRUD complet (+30 % efficacité opérationnelle).',
      'Caching Laravel, réduction du temps de chargement de 35 %.',
    ],
    tags: ['Laravel', 'MySQL', 'Tailwind CSS'],
  },
  {
    title: 'Développeur Laravel Stagiaire',
    type: 'Stage',
    date: 'Nov. 2025 – Présent',
    company: 'Go Digital Technology — Cotonou',
    dotColor: 'var(--dark)',
    highlights: [
      'Développement et maintenance des projets clés avec Laravel.',
      'Intégration d\'API RESTful et amélioration de 15 % des performances.',
      'Participation aux sprints et réunions quotidiennes (Agile/Scrum).',
    ],
    tags: ['Laravel', 'API REST', 'Git'],
  },
  {
    title: 'Site vitrine New Béthel',
    type: 'Freelance',
    date: 'Août – Sept. 2025',
    company: null,
    dotColor: 'var(--red)',
    highlights: [
      'Site officiel de la New Bethel International School.',
      'Front-end 100 % responsive + tableau de bord admin complet.',
      'Optimisation des requêtes : +40 % vitesse de chargement.',
    ],
    tags: ['Laravel', 'Tailwind CSS', 'MySQL'],
  },
  {
    title: 'Simulateur de coût ATL',
    type: 'Freelance',
    date: 'Juillet 2025',
    company: null,
    dotColor: 'var(--dark)',
    highlights: [
      'Outil de simulation des coûts de transport pour ATL.',
      'Calculs en temps réel améliorant la prise de décision de 70 %.',
    ],
    tags: ['PHP', 'Bootstrap', 'SQLite'],
  },
]
</script>

<style scoped>
.exp-list {
  max-width: 750px;
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  gap: 0.75rem;
}

.exp-item {
  background: var(--bg-card);
  border: 1px solid var(--border-light);
  border-radius: 14px;
  overflow: hidden;
  transition: var(--ease);
}

.exp-item.open {
  border-color: rgba(221, 45, 74, 0.15);
}

.exp-header {
  width: 100%;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1.25rem 1.5rem;
  background: none;
  border: none;
  cursor: pointer;
  font-family: inherit;
  text-align: left;
  color: inherit;
}

.exp-header-left {
  display: flex;
  align-items: center;
  gap: 1rem;
}

.exp-dot {
  width: 10px;
  height: 10px;
  border-radius: 50%;
  flex-shrink: 0;
}

.exp-header h3 {
  font-size: 1rem;
  margin-bottom: 0.1rem;
  color: var(--dark);
}

.exp-meta {
  font-size: 0.8rem;
  color: var(--text-muted);
}

.exp-chevron {
  color: var(--text-muted);
  font-size: 0.8rem;
  transition: transform 0.3s ease;
}

.exp-item.open .exp-chevron {
  transform: rotate(180deg);
  color: var(--red);
}

.exp-details {
  padding: 0 1.5rem 1.5rem 3rem;
}

.exp-company {
  color: var(--text-muted);
  font-size: 0.85rem;
  margin-bottom: 0.75rem;
  display: flex;
  align-items: center;
  gap: 0.4rem;
}

.exp-company i {
  color: var(--red);
  font-size: 0.8rem;
}

.exp-points {
  margin-bottom: 0.75rem;
  list-style: none;
}

.exp-points li {
  position: relative;
  padding-left: 1rem;
  margin-bottom: 0.3rem;
  font-size: 0.85rem;
  color: var(--text-muted);
  line-height: 1.5;
}

.exp-points li::before {
  content: '–';
  position: absolute;
  left: 0;
  color: var(--red);
  font-weight: 700;
}

.exp-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.3rem;
}

@media (max-width: 768px) {
  .exp-header {
    padding: 1rem;
  }

  .exp-details {
    padding: 0 1rem 1rem 2.5rem;
  }
}
</style>
