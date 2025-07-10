<template>
  <div :class="{ 'bg-white': !nightMode, 'bg-dark': nightMode }" class="p-st">
    <div class="container py-4">
      <div
        class="text-center"
        data-aos="fade"
        data-aos-once="true"
        data-aos-duration="1000"
      >
        <span
          class="title text-center"
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
  font-size: 30px;
  font-weight: 500;
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

.text-dark {
  color: #111;
}

.skill-card {
  border-radius: 8px;
  width: 100%;
  height: 100px;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 10px;
  transition: all 0.3s ease-in-out;
  cursor: default;
}

/* Mode Terang */
.skill-light {
  background-color: #f9f9f9;
  color: #111;
  border: 1px solid #ccc;
}
.skill-light:hover {
  transform: scale(1.05);
  box-shadow: 0 0 8px rgba(0, 0, 0, 0.1);
}

/* Mode Gelap */
.skill-dark {
  background-color: #111;
  color: #00f0ff;
  border: 1px solid #00f0ff;
}
.skill-dark:hover {
  transform: scale(1.05);
  box-shadow: 0 0 12px #00f0ff;
}

.skill-icon {
  width: 24px;
  height: 24px;
  filter: brightness(1.2) drop-shadow(0 0 4px #00f0ff);
}
</style>
