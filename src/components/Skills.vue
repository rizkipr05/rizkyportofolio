<template>
  <div :class="{ 'skills-dark': nightMode }" class="p-st skills-section">
    <div class="container skills-shell py-5">
      <div
        class="section-head"
        data-aos="fade"
        data-aos-once="true"
        data-aos-duration="1000"
      >
        <div class="skills-heading">
          <span class="section-kicker">Technical stack</span>
          <h2
            class="title"
            :class="{ 'text-dark': !nightMode, 'text-light': nightMode }"
          >
            Fullstack tools I use to design, build, and ship products.
          </h2>
          <p class="skills-intro">
            From interface work to backend services and database design, this is the stack behind the products I build.
          </p>
        </div>

        <div class="stack-highlight">
          <div class="stack-label">Core stack</div>
          <div class="stack-pills">
            <span class="stack-pill">Laravel</span>
            <span class="stack-pill">React</span>
            <span class="stack-pill">Vue</span>
            <span class="stack-pill">Node.js</span>
            <span class="stack-pill">PostgreSQL</span>
            <span class="stack-pill">MySQL</span>
            <span class="stack-pill">MongoDB</span>
          </div>
        </div>
      </div>

      <div class="skills-grid">
        <div
          v-for="(skill, index) in skills"
          :key="skill.title"
          class="skill-card-wrap"
          :data-aos="'fade-up'"
          :data-aos-delay="index * 70"
        >
          <div class="skill-card" :class="{ 'skill-light': !nightMode, 'skill-dark': nightMode }">
            <div class="skill-badge">{{ getCategory(skill.title) }}</div>
            <div class="skill-icon-wrap">
              <img
                :src="skill.icon"
                :alt="skill.title"
                class="skill-icon"
              />
            </div>
            <div class="skill-copy">
              <strong>{{ skill.title }}</strong>
              <span>{{ getDescription(skill.title) }}</span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import info from "../../info";
import AOS from "aos";
import "aos/dist/aos.css";

const skillMeta = {
  HTML: {
    category: "Frontend",
    description: "Semantic page structure and accessible markup.",
  },
  CSS: {
    category: "Frontend",
    description: "Responsive layouts, motion, and polished visual systems.",
  },
  PHP: {
    category: "Backend",
    description: "Server-side application logic and business workflows.",
  },
  Javascript: {
    category: "Language",
    description: "Core language for interactive interfaces and app logic.",
  },
  Laravel: {
    category: "Backend",
    description: "Structured APIs, authentication, and scalable app architecture.",
  },
  VueJS: {
    category: "Frontend",
    description: "Reactive UI development for fast and maintainable products.",
  },
  NodeJS: {
    category: "Backend",
    description: "Event-driven services, APIs, and integration flows.",
  },
  Tailwind: {
    category: "Frontend",
    description: "Utility-first styling for rapid, consistent interfaces.",
  },
  Bootstrap: {
    category: "UI System",
    description: "Component-based layouts for quick delivery and responsiveness.",
  },
  ReactJS: {
    category: "Frontend",
    description: "Dynamic product interfaces and reusable component systems.",
  },
  "Next.js": {
    category: "Frontend",
    description: "App routing, SSR, and modern React production workflows.",
  },
  TypeScript: {
    category: "Language",
    description: "Safer codebases with stronger typing and maintainability.",
  },
  Flutter: {
    category: "Mobile",
    description: "Cross-platform mobile development from a single codebase.",
  },
  MySQL: {
    category: "Database",
    description: "Relational database design for transactional app data.",
  },
  PostgreSQL: {
    category: "Database",
    description: "Reliable data modeling, querying, and production-grade storage.",
  },
  MongoDB: {
    category: "Database",
    description: "Flexible document storage for fast-moving application needs.",
  },
};

export default {
  name: "Skills",
  props: {
    nightMode: Boolean,
  },
  data() {
    return {
      skills: info.skills,
    };
  },
  mounted() {
    AOS.init();
  },
  methods: {
    getCategory(title) {
      return skillMeta[title]?.category || "Stack";
    },
    getDescription(title) {
      return skillMeta[title]?.description || "Part of the stack I use in product development.";
    },
  },
};
</script>

<style scoped>
.skills-section {
  position: relative;
  overflow: hidden;
  padding: 28px 0 84px;
}

.skills-section::before {
  content: "";
  position: absolute;
  inset: 8% auto auto -8%;
  width: 320px;
  height: 320px;
  border-radius: 50%;
  background: radial-gradient(circle, rgba(56, 189, 248, 0.2), transparent 70%);
  pointer-events: none;
}

.skills-section::after {
  content: "";
  position: absolute;
  top: 4%;
  right: -6%;
  width: 360px;
  height: 360px;
  border-radius: 50%;
  background: radial-gradient(circle, rgba(129, 140, 248, 0.16), transparent 72%);
  pointer-events: none;
}

.skills-shell {
  position: relative;
  z-index: 1;
}

.section-head {
  display: grid;
  grid-template-columns: minmax(0, 1.1fr) minmax(300px, 0.9fr);
  gap: 28px;
  align-items: end;
  margin-bottom: 34px;
}

.section-kicker {
  display: inline-flex;
  align-items: center;
  padding: 0.58rem 0.92rem;
  border-radius: 999px;
  background: rgba(14, 165, 233, 0.12);
  color: #0369a1;
  font-size: 0.78rem;
  font-weight: 700;
  letter-spacing: 0.08em;
  text-transform: uppercase;
}

.title {
  margin: 18px 0 14px;
  font-size: clamp(2.5rem, 4vw, 4.1rem);
  line-height: 0.98;
  font-weight: 700;
  max-width: 10.5ch;
}

.skills-intro {
  max-width: 600px;
  margin: 0;
  font-size: 1rem;
  line-height: 1.85;
  color: #5f6f87;
}

.stack-highlight {
  padding: 24px;
  border-radius: 30px;
  background: linear-gradient(180deg, rgba(255, 255, 255, 0.84), rgba(245, 248, 255, 0.74));
  border: 1px solid rgba(148, 163, 184, 0.18);
  box-shadow: 0 26px 60px rgba(15, 23, 42, 0.08);
}

.stack-label {
  font-family: "Space Grotesk", sans-serif;
  font-size: 0.95rem;
  font-weight: 700;
  color: #0f172a;
  margin-bottom: 14px;
}

.stack-pills {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
}

.stack-pill {
  display: inline-flex;
  align-items: center;
  padding: 0.62rem 0.92rem;
  border-radius: 999px;
  background: rgba(14, 165, 233, 0.08);
  border: 1px solid rgba(14, 165, 233, 0.12);
  color: #075985;
  font-size: 0.84rem;
  font-weight: 700;
}

.skills-grid {
  display: grid;
  grid-template-columns: repeat(4, minmax(0, 1fr));
  gap: 18px;
}

.skill-card-wrap:nth-child(5n + 1) .skill-card,
.skill-card-wrap:nth-child(5n + 4) .skill-card {
  transform: translateY(18px);
}

.skill-card {
  position: relative;
  height: 100%;
  min-height: 220px;
  padding: 22px;
  border-radius: 28px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  gap: 18px;
  overflow: hidden;
  transition: transform 0.3s ease, box-shadow 0.3s ease, border-color 0.3s ease;
}

.skill-light {
  background: linear-gradient(180deg, rgba(255, 255, 255, 0.86), rgba(246, 249, 255, 0.76));
  border: 1px solid rgba(148, 163, 184, 0.18);
  box-shadow: 0 20px 44px rgba(15, 23, 42, 0.08);
}

.skill-dark {
  background: linear-gradient(180deg, rgba(13, 24, 40, 0.92), rgba(9, 16, 30, 0.84));
  border: 1px solid rgba(125, 211, 252, 0.12);
  box-shadow: 0 24px 52px rgba(2, 8, 23, 0.28);
}

.skill-card:hover {
  transform: translateY(-8px) !important;
}

.skill-light:hover {
  box-shadow: 0 30px 60px rgba(15, 23, 42, 0.12);
  border-color: rgba(14, 165, 233, 0.2);
}

.skill-dark:hover {
  box-shadow: 0 30px 60px rgba(2, 132, 199, 0.16);
  border-color: rgba(125, 211, 252, 0.18);
}

.skill-badge {
  display: inline-flex;
  align-self: flex-start;
  padding: 0.46rem 0.76rem;
  border-radius: 999px;
  background: rgba(14, 165, 233, 0.1);
  color: #0369a1;
  font-size: 0.74rem;
  font-weight: 700;
  letter-spacing: 0.06em;
  text-transform: uppercase;
}

.skill-dark .skill-badge {
  background: rgba(56, 189, 248, 0.12);
  color: #7dd3fc;
}

.skill-icon-wrap {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 72px;
  height: 72px;
  border-radius: 20px;
  background: rgba(255, 255, 255, 0.72);
  box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.8);
}

.skill-dark .skill-icon-wrap {
  background: rgba(255, 255, 255, 0.05);
  box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.04);
}

.skill-icon {
  width: 42px;
  height: 42px;
  filter: drop-shadow(0 12px 20px rgba(14, 165, 233, 0.2));
}

.skill-copy {
  display: flex;
  flex-direction: column;
  gap: 8px;
}

.skill-copy strong {
  font-family: "Space Grotesk", sans-serif;
  font-size: 1.08rem;
  font-weight: 700;
  color: #0f172a;
}

.skill-dark .skill-copy strong {
  color: #f8fbff;
}

.skill-copy span {
  font-size: 0.9rem;
  line-height: 1.7;
  color: #5f6f87;
}

.skill-dark .skill-copy span {
  color: rgba(231, 238, 252, 0.72);
}

@media only screen and (max-width: 1199px) {
  .skills-grid {
    grid-template-columns: repeat(3, minmax(0, 1fr));
  }
}

@media only screen and (max-width: 991px) {
  .section-head {
    grid-template-columns: 1fr;
  }

  .title {
    max-width: none;
  }

  .skills-grid {
    grid-template-columns: repeat(2, minmax(0, 1fr));
  }

  .skill-card-wrap:nth-child(5n + 1) .skill-card,
  .skill-card-wrap:nth-child(5n + 4) .skill-card {
    transform: none;
  }
}

@media only screen and (max-width: 580px) {
  .skills-section {
    padding: 12px 0 60px;
  }

  .skills-grid {
    grid-template-columns: 1fr;
  }

  .skill-card {
    min-height: 196px;
  }

  .stack-highlight {
    padding: 20px;
  }
}
</style>
