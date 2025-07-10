[media pointer="file-service://file-Hthhp76ZiycxJLQ6m4AveK"]
<template>
  <div :class="{ 'bg-white': !nightMode, 'bg-dark': nightMode }" class="pt-5 p-st">
    <div class="container" data-aos="fade" data-aos-once="true" data-aos-duration="1000">
      <div class="row align-items-center">
        <div class="col-xl-6 col-bg-6 col-md-6 col-sm-12 text-center" data-aos="fade-right" data-aos-duration="1200">
          <img :src="picture" class="profile-image" />
        </div>
        <div class="col-xl-6 col-bg-6 col-md-6 col-sm-12 pt-5" data-aos="fade-left" data-aos-duration="1200">
          <span class="home-title" :class="{ 'text-dark': !nightMode, 'text-light': nightMode }">
            Welcome to my portfolio!
          </span>
          <div data-aos="fade-left" data-aos-delay="400">
            <p v-html="description"></p>
          </div>
          <div class="text-center pb-4">
            <button class="btn btn-outline-secondary mx-2 aos-btn" @click="open('linkedin')" v-tooltip.bottom="'LinkedIn'" data-aos="zoom-in" data-aos-delay="600">
              <i class="fab fa-linkedin"></i>
            </button>
            <button class="btn btn-outline-secondary mx-2 aos-btn" @click="open('github')" v-tooltip.bottom="'GitHub'" data-aos="zoom-in" data-aos-delay="700">
              <i class="fab fa-github"></i>
            </button>
            <button class="btn btn-outline-secondary mx-2 aos-btn" @click="open('resume')" v-tooltip.bottom="'Resume'" data-aos="zoom-in" data-aos-delay="800">
              <i class="fa fa-file"></i>
            </button>
          </div>
        </div>
      </div>

      <!-- GitHub Contribution Chart -->
      <div class="text-center contribution-section" data-aos="fade-up" data-aos-delay="300">
        <h4 :class="{ 'text-dark': !nightMode, 'text-light': nightMode }">
          My GitHub Contribution Activity
        </h4>
        <div class="github-chart-wrapper">
          <img
            :src="`https://ghchart.rshah.org/${githubUsername}`"
            alt="GitHub Contributions"
            class="github-chart"
          />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import info from "../../info";
import AOS from "aos";
import "aos/dist/aos.css";
import Wave from "./helpers/Wave";

export default {
  name: "Home",

  components: {
    Wave,
  },
  props: {
    nightMode: {
      type: Boolean,
    },
  },
  data() {
    return {
      picture: info.flat_picture,
      description: info.description,
      name: info.name,
      linkedin: info.links.linkedin,
      github: info.links.github,
      resume: info.links.resume,
      githubUsername: "rizkipr05",
    };
  },
  mounted() {
    AOS.init();
  },
  methods: {
    open(link) {
      const urls = {
        linkedin: this.linkedin,
        github: this.github,
        resume: this.resume,
      };
      if (urls[link]) window.open(urls[link], "_blank");
    },
  },
};
</script>

<style scoped>
@keyframes slideFadeIn {
  0% {
    opacity: 0;
    transform: translateY(20px);
  }
  100% {
    opacity: 1;
    transform: translateY(0);
  }
}

.home-title {
  font-size: 32px;
  font-weight: 500;
  animation: slideFadeIn 1s ease-out forwards;
  animation-delay: 0.3s;
  opacity: 0;
  will-change: opacity, transform;
}

.profile-image {
  max-width: 800px;
  max-height: 500px;
  margin-top: 80px;
  transform: rotateY(180deg);
  transition: transform 0.4s ease, filter 0.4s ease;
}
.profile-image:hover {
  transform: rotateY(180deg) scale(1.03);
  filter: brightness(1.1);
}

@media only screen and (max-width: 580px) {
  .profile-image {
    object-fit: cover;
    border-radius: 50%;
    height: 200px;
    width: 200px;
    margin-top: 10px;
    margin-bottom: 10px;
    border: 2px solid rgb(205, 205, 205);
  }
}

.text-dark {
  color: #1a1a1a;
}
.text-light {
  color: #f1f1f1;
}

.fa {
  font-size: 15px;
}

.btn {
  border-color: #759CC9;
  color: #759CC9;
  transition: all 0.3s ease;
}
.btn:hover {
  background-color: #759CC9;
  border-color: #759CC9;
  color: white;
  transform: scale(1.05);
}
.btn:focus {
  background-color: #759CC9;
  border-color: #759CC9;
  color: white;
  outline: none !important;
}

p {
  text-align: justify;
  font-weight: 400;
}

/* Contribution Chart Styling */
.contribution-section {
  margin-top: 80px;
  padding-bottom: 0;
  margin-bottom: 0;
  background-color: transparent;
}

.github-chart-wrapper {
  margin-top: 20px;
  padding: 20px;
  background-color: transparent;
  border-radius: 10px;
}

.github-chart {
  max-width: 100%;
  display: block;
  margin: 0 auto;
  border-radius: 10px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
  transition: filter 0.3s ease;
}

.bg-dark .github-chart {
  filter: invert(1) hue-rotate(180deg);
}
</style>  