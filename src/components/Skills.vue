<template>
  <div :class="{ 'skills-dark': nightMode }" class="p-st skills-section">
    <div class="container py-5">
      <div
        class="text-center section-head"
        data-aos="fade"
        data-aos-once="true"
        data-aos-duration="1000"
      >
        <span
          class="section-kicker"
        >
          Technical stack
        </span>
        <span
          class="title text-center d-block mt-2"
          :class="{ 'text-dark': !nightMode, 'text-light': nightMode }"
        >
          Skills
        </span>
      </div>
      <hr
        width="50%"
        :class="{ pgray: !nightMode, 'bg-secondary': nightMode }"
      />
      <br />
      <div class="row justify-content-center">
        <div
          v-for="(skill, index) in skills"
          :key="skill.title"
          class="col-lg-3 col-md-4 col-sm-6 mb-4 d-flex justify-content-center"
          :data-aos="'fade-up'"
          :data-aos-delay="index * 100"
        >
          <div
            class="text-center p-3 skill-card"
            :class="{ 'skill-light': !nightMode, 'skill-dark': nightMode }"
          >
            <img
              :src="skill.icon"
              :alt="skill.title"
              class="skill-icon"
            />
            <span>{{ skill.title }}</span>
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
};
</script>

<style scoped>
.title {
  font-size: 2.4rem;
  font-weight: 700;
}
.title1 {
  font-size: 24px;
  font-weight: 400;
}
.title2 {
  font-size: 20px;
  font-weight: 500;
}
.title3 {
  font-size: 16px;
  font-weight: 400;
}

.section-head {
  margin-bottom: 18px;
}

.section-kicker {
  display: inline-block;
  padding: 0.45rem 0.85rem;
  border-radius: 999px;
  background: rgba(14, 165, 233, 0.12);
  color: #0369a1;
  font-size: 0.8rem;
  font-weight: 700;
  letter-spacing: 0.08em;
  text-transform: uppercase;
}

.skills-section {
  position: relative;
}

.skills-section::before {
  content: "";
  position: absolute;
  inset: 10% auto auto -10%;
  width: 280px;
  height: 280px;
  border-radius: 50%;
  background: radial-gradient(circle, rgba(14, 165, 233, 0.18), transparent 70%);
  pointer-events: none;
}

.skill-card {
  border-radius: 24px;
  width: 100%;
  min-height: 132px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 14px;
  transition: all 0.3s ease-in-out;
  cursor: default;
  border: 1px solid rgba(148, 163, 184, 0.18);
  box-shadow: 0 18px 45px rgba(15, 23, 42, 0.08);
}

.skill-light {
  background: rgba(255, 255, 255, 0.72);
  color: #111;
}
.skill-light:hover {
  transform: translateY(-6px);
  box-shadow: 0 24px 55px rgba(15, 23, 42, 0.12);
}

.skill-dark {
  background: rgba(255, 255, 255, 0.04);
  color: #dbeafe;
  border-color: rgba(125, 211, 252, 0.12);
}
.skill-dark:hover {
  transform: translateY(-6px);
  box-shadow: 0 24px 55px rgba(2, 132, 199, 0.14);
}

.skill-icon {
  width: 38px;
  height: 38px;
  filter: drop-shadow(0 10px 18px rgba(14, 165, 233, 0.22));
}

.skill-card span {
  font-family: "Space Grotesk", sans-serif;
  font-weight: 600;
  font-size: 1rem;
}
</style>
