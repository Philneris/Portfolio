<template>
  <section id="accueil" class="hero">
    <!-- Decorative colored shapes -->
    <div class="hero-decor">
      <div class="decor-shape shape-rose"></div>
      <div class="decor-shape shape-dark"></div>
    </div>

    <div class="container hero-grid">
      <!-- Left: Text -->
      <div class="hero-text">
        <div class="hero-badge">
          <span class="dot-pulse"></span>
          Disponible pour des projets
        </div>
        <h1>
          Je suis <span class="highlight-rose">Néris</span>,<br>
          Développeur<br>
          <span class="typed-text">{{ currentText }}<span class="cursor-blink">|</span></span>
        </h1>
        <p>
          Développeur Full-Stack axé sur les résultats avec plus de 2 ans d'expérience,
          spécialisé dans la création d'applications web performantes et évolutives.
        </p>
        <div class="hero-actions">
          <a href="#projets" class="btn btn-primary">
            <i class="fas fa-rocket"></i> Voir mes projets
          </a>
          <a href="#contact" class="btn btn-outline">
            <i class="fas fa-envelope"></i> Me contacter
          </a>
        </div>
        <div class="hero-stats">
          <div class="stat">
            <span class="stat-number">2+</span>
            <span class="stat-label">Années d'exp.</span>
          </div>
          <div class="stat-divider"></div>
          <div class="stat">
            <span class="stat-number">4+</span>
            <span class="stat-label">Projets livrés</span>
          </div>
          <div class="stat-divider"></div>
          <div class="stat">
            <span class="stat-number">100%</span>
            <span class="stat-label">Satisfaction</span>
          </div>
        </div>
      </div>

      <!-- Right: Image -->
      <div class="hero-visual">
        <div class="blob-wrapper">
          <div class="blob-ring"></div>
          <div class="blob">
            <img src="/maphoto.png" alt="Néris Assogbadjo" class="profile-photo" />
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const words = ['web', 'Full-Stack', 'Laravel', 'Vue.js']
const currentText = ref('')
let wordIndex = 0
let charIndex = 0
let isDeleting = false
let timer = null

const type = () => {
  const currentWord = words[wordIndex]
  if (!isDeleting) {
    currentText.value = currentWord.substring(0, charIndex + 1)
    charIndex++
    if (charIndex === currentWord.length) {
      isDeleting = true
      timer = setTimeout(type, 2000)
      return
    }
  } else {
    currentText.value = currentWord.substring(0, charIndex - 1)
    charIndex--
    if (charIndex === 0) {
      isDeleting = false
      wordIndex = (wordIndex + 1) % words.length
    }
  }
  timer = setTimeout(type, isDeleting ? 50 : 120)
}

onMounted(() => { timer = setTimeout(type, 500) })
onUnmounted(() => { clearTimeout(timer) })
</script>

<style scoped>
.hero {
  min-height: 100vh;
  display: flex;
  align-items: center;
  padding-top: 80px;
  overflow: hidden;
  background: var(--bg-main);
  position: relative;
}

/* -- Decorative BG Shapes -- */
.hero-decor {
  position: absolute;
  inset: 0;
  pointer-events: none;
  z-index: 0;
}

.decor-shape {
  position: absolute;
  border-radius: 50%;
  filter: blur(100px);
}

.shape-rose {
  width: 450px;
  height: 450px;
  background: rgba(221, 45, 74, 0.07);
  top: -10%;
  right: -5%;
}

.shape-dark {
  width: 350px;
  height: 350px;
  background: rgba(48, 50, 61, 0.05);
  bottom: 0;
  left: -5%;
}

/* -- Grid -- */
.hero-grid {
  display: grid;
  grid-template-columns: 1.1fr 0.9fr;
  gap: 4rem;
  align-items: center;
  position: relative;
  z-index: 1;
}

/* -- Badge -- */
.hero-badge {
  display: inline-flex;
  align-items: center;
  gap: 0.6rem;
  background: rgba(221, 45, 74, 0.06);
  border: 1px solid rgba(221, 45, 74, 0.15);
  padding: 0.45rem 1.2rem;
  border-radius: 50px;
  font-size: 0.8rem;
  font-weight: 600;
  color: var(--red);
  margin-bottom: 1.5rem;
  animation: fadeInUp 0.6s ease both;
}

.dot-pulse {
  width: 8px;
  height: 8px;
  background: var(--red);
  border-radius: 50%;
}

/* -- Text -- */
.hero-text h1 {
  font-size: 3.8rem;
  line-height: 1.15;
  margin-bottom: 1.5rem;
  color: var(--dark);
  animation: fadeInUp 0.6s ease 0.2s both;
}

.highlight-rose {
  color: var(--red);
}

.typed-text {
  color: var(--red);
}

.cursor-blink {
  animation: blink 0.8s infinite;
  color: var(--red);
}

@keyframes blink {
  0%, 100% { opacity: 1; }
  50% { opacity: 0; }
}

.hero-text p {
  color: var(--text-muted);
  font-size: 1.1rem;
  max-width: 500px;
  margin-bottom: 2.5rem;
  animation: fadeInUp 0.6s ease 0.4s both;
}

/* -- Actions -- */
.hero-actions {
  display: flex;
  gap: 1rem;
  flex-wrap: wrap;
  margin-bottom: 3rem;
  animation: fadeInUp 0.6s ease 0.6s both;
}

/* -- Stats -- */
.hero-stats {
  display: flex;
  align-items: center;
  gap: 2rem;
  animation: fadeInUp 0.6s ease 0.8s both;
}

.stat-number {
  display: block;
  font-family: 'Space Grotesk', sans-serif;
  font-size: 1.8rem;
  font-weight: 800;
  color: var(--red);
}

.stat-label {
  font-size: 0.8rem;
  color: var(--text-muted);
}

.stat-divider {
  width: 1px;
  height: 40px;
  background: var(--border-light);
}

/* -- Visual / Blob -- */
.hero-visual {
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
  animation: fadeInUp 0.6s ease 0.3s both;
}

.blob-wrapper {
  position: relative;
}

/* Single deformed ring */
.blob-ring {
  position: absolute;
  inset: -25px;
  border: 2px solid rgba(221, 45, 74, 0.15);
  border-radius: 42% 58% 70% 30% / 45% 45% 55% 55%;
}

.blob {
  width: 370px;
  height: 370px;
  background: rgba(221, 45, 74, 0.03);
  border: 3px solid rgba(221, 45, 74, 0.2);
  border-radius: 42% 58% 70% 30% / 45% 45% 55% 55%;
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
  position: relative;
}

.profile-photo {
  width: 100%;
  height: 100%;
  object-fit: contain;
  object-position: center center;
  position: relative;
  z-index: 1;
}

/* -- Responsive -- */
@media (max-width: 992px) {
  .hero-grid {
    grid-template-columns: 1fr;
    text-align: center;
  }

  /* Photo on top on mobile */
  .hero-visual {
    order: -1;
  }

  .hero-text h1 {
    font-size: 2.8rem;
  }

  .hero-text p {
    margin-left: auto;
    margin-right: auto;
  }

  .hero-actions {
    justify-content: center;
  }

  .hero-stats {
    justify-content: center;
  }

  .blob {
    width: 260px;
    height: 260px;
  }

  .blob-ring {
    inset: -18px;
  }

  .hero-badge {
    margin-left: auto;
    margin-right: auto;
  }

  .shape-rose { width: 250px; height: 250px; }
  .shape-dark { width: 200px; height: 200px; }
}

@media (max-width: 480px) {
  .hero-text h1 {
    font-size: 2.2rem;
  }

  .hero-stats {
    gap: 1.5rem;
  }

  .stat-number {
    font-size: 1.5rem;
  }
}
</style>
