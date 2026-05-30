<template>
  <section
    class="p-st about-section"
    :class="{
      'bg-light': !nightMode,
      'bg-dark2': nightMode,
      'text-light': nightMode,
    }"
  >
    <div class="container about-shell py-5">
      <div
        class="section-head"
        data-aos="fade"
        data-aos-once="true"
        data-aos-duration="1000"
      >
        <div class="about-copy">
          <span class="section-kicker">Career timeline</span>
          <h2
            class="title"
            :class="{ 'text-dark': !nightMode, 'text-light': nightMode }"
          >
            Education, experience, and the path behind the work.
          </h2>
          <p class="section-description">
            My background combines formal study, production work, freelance delivery, and applied AI projects.
          </p>
        </div>

        <div class="about-panel">
          <div class="panel-label">Current focus</div>
          <div class="focus-list">
            <span>Fullstack apps</span>
            <span>Machine learning</span>
            <span>Product-oriented UI</span>
            <span>Scalable backend systems</span>
          </div>
        </div>
      </div>

      <div class="timeline-grid">
        <div class="timeline-column">
          <Timeline :data="education" :nightMode="nightMode" />
        </div>
        <div class="timeline-column">
          <Timeline :data="experience" :nightMode="nightMode" />
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import Timeline from "./helpers/Timeline";
import info from "../../info";

export default {
  name: "About",
  components: {
    Timeline,
  },
  props: {
    nightMode: {
      type: Boolean,
    },
  },
  data() {
    return {
      education: {
        title: "education",
        data: info.education,
      },
      experience: {
        title: "experiences",
        data: info.experience,
      },
    };
  },
};
</script>

<style scoped>
.about-section {
  position: relative;
  overflow: hidden;
  padding: 40px 0 84px;
}

.about-section::before {
  content: "";
  position: absolute;
  top: 10%;
  left: -8%;
  width: 320px;
  height: 320px;
  border-radius: 50%;
  background: radial-gradient(circle, rgba(56, 189, 248, 0.18), transparent 70%);
  pointer-events: none;
}

.about-section::after {
  content: "";
  position: absolute;
  right: -6%;
  bottom: 8%;
  width: 320px;
  height: 320px;
  border-radius: 50%;
  background: radial-gradient(circle, rgba(129, 140, 248, 0.14), transparent 72%);
  pointer-events: none;
}

.about-shell {
  position: relative;
  z-index: 1;
}

.section-head {
  display: grid;
  grid-template-columns: minmax(0, 1.1fr) minmax(280px, 0.9fr);
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
  font-size: clamp(2.4rem, 4vw, 4rem);
  line-height: 1;
  font-weight: 700;
  max-width: 11ch;
}

.section-description {
  max-width: 620px;
  margin: 0;
  color: #5f6f87;
  line-height: 1.85;
}

.about-panel {
  padding: 24px;
  border-radius: 30px;
  background: linear-gradient(180deg, rgba(255, 255, 255, 0.84), rgba(244, 247, 255, 0.74));
  border: 1px solid rgba(148, 163, 184, 0.18);
  box-shadow: 0 24px 56px rgba(15, 23, 42, 0.08);
}

.bg-dark2 .about-panel {
  background: linear-gradient(180deg, rgba(14, 24, 40, 0.92), rgba(9, 16, 29, 0.86));
  border-color: rgba(125, 211, 252, 0.1);
  box-shadow: 0 24px 56px rgba(2, 8, 23, 0.24);
}

.panel-label {
  font-family: "Space Grotesk", sans-serif;
  font-size: 0.95rem;
  font-weight: 700;
  margin-bottom: 14px;
}

.focus-list {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
}

.focus-list span {
  display: inline-flex;
  align-items: center;
  padding: 0.62rem 0.9rem;
  border-radius: 999px;
  background: rgba(14, 165, 233, 0.08);
  border: 1px solid rgba(14, 165, 233, 0.12);
  color: #075985;
  font-size: 0.84rem;
  font-weight: 700;
}

.bg-dark2 .focus-list span {
  background: rgba(56, 189, 248, 0.1);
  border-color: rgba(125, 211, 252, 0.12);
  color: #7dd3fc;
}

.timeline-grid {
  display: grid;
  grid-template-columns: repeat(2, minmax(0, 1fr));
  gap: 24px;
}

.timeline-column {
  padding: 8px;
  border-radius: 34px;
  background: rgba(255, 255, 255, 0.42);
  border: 1px solid rgba(148, 163, 184, 0.14);
  box-shadow: 0 24px 60px rgba(15, 23, 42, 0.05);
}

.bg-dark2 .timeline-column {
  background: rgba(255, 255, 255, 0.03);
  border-color: rgba(125, 211, 252, 0.08);
  box-shadow: 0 24px 60px rgba(2, 8, 23, 0.2);
}

@media only screen and (max-width: 991px) {
  .section-head,
  .timeline-grid {
    grid-template-columns: 1fr;
  }

  .title {
    max-width: none;
  }
}

@media only screen and (max-width: 580px) {
  .about-section {
    padding: 24px 0 60px;
  }
}
</style>
