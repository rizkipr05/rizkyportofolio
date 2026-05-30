[media pointer="file-service://file-Hthhp76ZiycxJLQ6m4AveK"]
<template>
  <div :class="{ 'hero-dark': nightMode }" class="hero-section pt-5 p-st">
    <div class="container hero-shell" data-aos="fade" data-aos-once="true" data-aos-duration="1000">
      <div class="hero-backdrop"></div>
      <div class="row align-items-center hero-grid">
        <div
          class="col-xl-5 col-lg-6 col-md-12 col-sm-12 hero-visual"
          data-aos="fade-right"
          data-aos-duration="1200"
        >
          <div class="orb orb-one"></div>
          <div class="orb orb-two"></div>
          <div class="portrait-stage">
            <div class="portrait-card">
              <div class="portrait-meta">
                <span class="meta-label">Available for freelance</span>
                <span class="meta-dot"></span>
              </div>
              <img :src="picture" class="profile-image" />
              <div class="portrait-footer">
                <div>
                  <p class="portrait-name">{{ name }}</p>
                  <span class="portrait-role">Web Developer & UI/UX Designer</span>
                </div>
                <div class="portrait-badge">ID</div>
              </div>
            </div>
            <div class="floating-card floating-card-top">
              <strong>Frontend + Product Design</strong>
              <span>Clean interface, solid implementation</span>
            </div>
            <div class="floating-card floating-card-bottom">
              <strong>Based in Bandar Lampung</strong>
              <span>Open to remote collaboration</span>
            </div>
          </div>
        </div>
        <div
          class="col-xl-7 col-lg-6 col-md-12 col-sm-12 pt-4 hero-copy"
          data-aos="fade-left"
          data-aos-duration="1200"
        >
          <div class="eyebrow">Software Developer • UI/UX Designer • AI Enthusiast</div>
          <span class="home-title" :class="{ 'text-dark': !nightMode, 'text-light': nightMode }">
            Designing sharp interfaces and building products that feel intentional.
          </span>
          <p class="hero-subtitle">
            I build modern web experiences with a product mindset: clean visuals, strong frontend execution, and practical engineering choices.
          </p>
          <div class="lead-copy" data-aos="fade-left" data-aos-delay="400">
            <p v-html="description"></p>
          </div>
          <div class="hero-insights" data-aos="fade-up" data-aos-delay="500">
            <div class="insight-card">
              <strong>3+ Years</strong>
              <span>Building websites, UI systems, and interactive products</span>
            </div>
            <div class="insight-card">
              <strong>React • Vue • Laravel</strong>
              <span>Comfortable from design direction to implementation</span>
            </div>
            <div class="insight-card">
              <strong>UI/UX + Code</strong>
              <span>Not just visuals. I turn ideas into shippable interfaces.</span>
            </div>
            <div class="insight-card">
              <strong>Student Builder</strong>
              <span>Learning fast, shipping often, and iterating in public.</span>
            </div>
          </div>
          <div class="hero-actions pb-3">
            <button class="btn btn-primary hero-btn mx-2 aos-btn" @click="open('linkedin')" v-tooltip.bottom="'LinkedIn'" data-aos="zoom-in" data-aos-delay="600">
              <i class="fab fa-linkedin"></i> Connect
            </button>
            <button class="btn btn-outline-secondary hero-btn mx-2 aos-btn" @click="open('github')" v-tooltip.bottom="'GitHub'" data-aos="zoom-in" data-aos-delay="700">
              <i class="fab fa-github"></i> Projects
            </button>
            <button class="btn btn-outline-secondary hero-btn mx-2 aos-btn" @click="open('resume')" v-tooltip.bottom="'Resume'" data-aos="zoom-in" data-aos-delay="800">
              <i class="fa fa-file"></i> Resume
            </button>
          </div>
          <div class="social-row">
            <button class="btn btn-outline-secondary social-btn mx-2 aos-btn" @click="open('linkedin')" v-tooltip.bottom="'LinkedIn'" data-aos="zoom-in" data-aos-delay="600">
              <i class="fab fa-linkedin"></i>
            </button>
            <button class="btn btn-outline-secondary social-btn mx-2 aos-btn" @click="open('github')" v-tooltip.bottom="'GitHub'" data-aos="zoom-in" data-aos-delay="700">
              <i class="fab fa-github"></i>
            </button>
            <button class="btn btn-outline-secondary social-btn mx-2 aos-btn" @click="open('resume')" v-tooltip.bottom="'Resume'" data-aos="zoom-in" data-aos-delay="800">
              <i class="fa fa-file"></i>
            </button>
          </div>
        </div>
      </div>

      <div class="contribution-strip" data-aos="fade-up" data-aos-delay="300">
        <div class="contribution-copy">
          <div class="section-chip">GitHub activity</div>
          <h4 :class="{ 'text-dark': !nightMode, 'text-light': nightMode }">
            Consistent output, visible progress, real iteration.
          </h4>
          <p>My contribution graph reflects how I work: keep shipping, keep refining, keep learning.</p>
        </div>
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

export default {
  name: "Home",
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

.hero-section {
  position: relative;
  padding-bottom: 64px;
}

.hero-shell {
  position: relative;
  padding: 44px;
  border-radius: 36px;
  background: linear-gradient(145deg, rgba(255, 255, 255, 0.82), rgba(248, 251, 255, 0.7));
  border: 1px solid rgba(148, 163, 184, 0.18);
  box-shadow: 0 30px 90px rgba(15, 23, 42, 0.12);
  overflow: hidden;
}

.hero-dark .hero-shell {
  background: linear-gradient(145deg, rgba(8, 17, 31, 0.92), rgba(10, 22, 40, 0.84));
  border-color: rgba(148, 163, 184, 0.12);
  box-shadow: 0 30px 80px rgba(0, 0, 0, 0.32);
}

.hero-backdrop {
  position: absolute;
  inset: 0;
  background:
    radial-gradient(circle at 14% 18%, rgba(56, 189, 248, 0.18), transparent 24%),
    radial-gradient(circle at 88% 22%, rgba(59, 130, 246, 0.14), transparent 24%),
    linear-gradient(180deg, rgba(255, 255, 255, 0.16), transparent 38%);
  pointer-events: none;
}

.hero-grid {
  min-height: 620px;
}

.hero-visual,
.hero-copy {
  position: relative;
  z-index: 1;
}

.portrait-stage {
  position: relative;
  max-width: 470px;
  margin: 0 auto;
  padding: 38px 18px 36px;
}

.portrait-card {
  position: relative;
  padding: 18px;
  border-radius: 34px;
  background: linear-gradient(180deg, rgba(255, 255, 255, 0.8), rgba(241, 246, 255, 0.62));
  border: 1px solid rgba(148, 163, 184, 0.18);
  box-shadow: 0 28px 70px rgba(15, 23, 42, 0.16);
  overflow: hidden;
}

.hero-dark .portrait-card {
  background: linear-gradient(180deg, rgba(255, 255, 255, 0.08), rgba(255, 255, 255, 0.04));
}

.portrait-card::before {
  content: "";
  position: absolute;
  inset: 0 auto auto 0;
  width: 100%;
  height: 120px;
  background: linear-gradient(135deg, rgba(14, 165, 233, 0.14), transparent 72%);
  pointer-events: none;
}

.portrait-meta,
.portrait-footer {
  position: relative;
  z-index: 1;
}

.portrait-meta {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 16px;
}

.meta-label {
  display: inline-flex;
  align-items: center;
  padding: 0.55rem 0.8rem;
  border-radius: 999px;
  background: rgba(14, 165, 233, 0.12);
  color: #0369a1;
  font-size: 0.75rem;
  font-weight: 700;
  letter-spacing: 0.08em;
  text-transform: uppercase;
}

.meta-dot {
  width: 14px;
  height: 14px;
  border-radius: 999px;
  background: linear-gradient(135deg, #22c55e, #84cc16);
  box-shadow: 0 0 0 8px rgba(34, 197, 94, 0.16);
}

.eyebrow {
  display: inline-flex;
  align-items: center;
  gap: 10px;
  padding: 0.62rem 0.96rem;
  border-radius: 999px;
  background: rgba(14, 165, 233, 0.1);
  color: #0369a1;
  font-size: 0.78rem;
  font-weight: 700;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  margin-bottom: 20px;
}

.home-title {
  display: block;
  font-size: clamp(2.7rem, 4.8vw, 5.2rem);
  line-height: 0.97;
  font-weight: 700;
  letter-spacing: -0.055em;
  max-width: 10.5ch;
  animation: slideFadeIn 1s ease-out forwards;
  animation-delay: 0.3s;
  opacity: 0;
  will-change: opacity, transform;
}

.hero-subtitle {
  max-width: 640px;
  margin: 18px 0 0;
  font-size: 1.08rem;
  line-height: 1.8;
  color: #334155;
}

.hero-dark .hero-subtitle {
  color: rgba(231, 238, 252, 0.8);
}

.lead-copy {
  margin-top: 18px;
  max-width: 680px;
}

.lead-copy p {
  font-size: 0.98rem;
  line-height: 1.88;
  color: #5f6f87;
}

.hero-dark .lead-copy p,
.hero-dark .contribution-copy p {
  color: rgba(231, 238, 252, 0.72);
}

.hero-insights {
  display: grid;
  grid-template-columns: repeat(2, minmax(0, 1fr));
  gap: 14px;
  margin: 30px 0;
}

.insight-card {
  display: flex;
  flex-direction: column;
  gap: 6px;
  min-height: 122px;
  padding: 18px 18px 16px;
  border-radius: 24px;
  background: rgba(255, 255, 255, 0.64);
  border: 1px solid rgba(148, 163, 184, 0.18);
  backdrop-filter: blur(8px);
  box-shadow: 0 12px 30px rgba(15, 23, 42, 0.06);
}

.hero-dark .insight-card {
  background: rgba(255, 255, 255, 0.04);
}

.insight-card strong {
  font-size: 1rem;
  font-family: "Space Grotesk", sans-serif;
}

.insight-card span {
  font-size: 0.88rem;
  line-height: 1.65;
  color: #5f6f87;
}

.hero-dark .insight-card span {
  color: rgba(231, 238, 252, 0.72);
}

.profile-image {
  position: relative;
  z-index: 1;
  display: block;
  width: 100%;
  height: 520px;
  object-fit: cover;
  object-position: center top;
  border-radius: 28px;
  transition: transform 0.4s ease, filter 0.4s ease;
  filter: saturate(1.02) contrast(1.02);
}
.profile-image:hover {
  transform: scale(1.02);
  filter: saturate(1.08) contrast(1.04);
}

.portrait-footer {
  display: flex;
  align-items: flex-end;
  justify-content: space-between;
  gap: 16px;
  margin-top: 18px;
}

.portrait-name {
  margin: 0;
  font-family: "Space Grotesk", sans-serif;
  font-size: 1.15rem;
  font-weight: 700;
  color: #0f172a;
}

.hero-dark .portrait-name {
  color: #f8fbff;
}

.portrait-role {
  font-size: 0.9rem;
  color: #64748b;
}

.portrait-badge {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  min-width: 54px;
  height: 54px;
  border-radius: 18px;
  background: linear-gradient(135deg, #0ea5e9, #2563eb);
  color: white;
  font-family: "Space Grotesk", sans-serif;
  font-weight: 700;
  letter-spacing: 0.08em;
}

.floating-card {
  position: absolute;
  z-index: 2;
  width: 220px;
  padding: 16px 18px;
  border-radius: 22px;
  background: rgba(255, 255, 255, 0.82);
  border: 1px solid rgba(148, 163, 184, 0.18);
  box-shadow: 0 20px 50px rgba(15, 23, 42, 0.12);
  backdrop-filter: blur(12px);
}

.hero-dark .floating-card {
  background: rgba(8, 17, 31, 0.74);
}

.floating-card strong {
  display: block;
  font-size: 0.92rem;
  font-family: "Space Grotesk", sans-serif;
  margin-bottom: 4px;
}

.floating-card span {
  display: block;
  font-size: 0.82rem;
  line-height: 1.5;
  color: #64748b;
}

.hero-dark .floating-card span {
  color: rgba(231, 238, 252, 0.72);
}

.floating-card-top {
  top: 0;
  right: -12px;
}

.floating-card-bottom {
  left: -14px;
  bottom: 8px;
}

.orb {
  position: absolute;
  border-radius: 999px;
  filter: blur(12px);
}

.orb-one {
  width: 300px;
  height: 300px;
  background: radial-gradient(circle, rgba(14, 165, 233, 0.26), transparent 70%);
  top: 10%;
  left: -8%;
}

.orb-two {
  width: 240px;
  height: 240px;
  background: radial-gradient(circle, rgba(37, 99, 235, 0.18), transparent 68%);
  bottom: 0;
  right: -2%;
}

.fa {
  font-size: 15px;
}

.hero-actions {
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  margin: 12px -8px 0;
}

.hero-btn,
.social-btn {
  border-radius: 999px;
  transition: all 0.3s ease;
}

.hero-btn {
  padding: 0.9rem 1.42rem;
  font-weight: 700;
  border-color: rgba(14, 165, 233, 0.26);
  color: #0369a1;
  background: rgba(255, 255, 255, 0.65);
}

.hero-btn.btn-primary {
  background: linear-gradient(135deg, #0ea5e9, #2563eb);
  border: none;
  color: white;
  box-shadow: 0 20px 40px rgba(37, 99, 235, 0.25);
}

.hero-btn:hover,
.social-btn:hover {
  transform: translateY(-3px);
}

.social-row {
  display: flex;
  align-items: center;
  margin: 6px -8px 0;
}

.social-btn {
  width: 46px;
  height: 46px;
  border-color: rgba(14, 165, 233, 0.2);
  color: #0369a1;
  background: rgba(255, 255, 255, 0.64);
}

.hero-dark .hero-btn,
.hero-dark .social-btn {
  background: rgba(255, 255, 255, 0.04);
  color: #7dd3fc;
  border-color: rgba(125, 211, 252, 0.16);
}

.btn:focus {
  color: white;
  outline: none !important;
}

.contribution-strip {
  position: relative;
  z-index: 1;
  margin-top: 30px;
  padding: 24px 26px;
  border-radius: 30px;
  background: rgba(255, 255, 255, 0.58);
  border: 1px solid rgba(148, 163, 184, 0.18);
  display: grid;
  grid-template-columns: minmax(260px, 0.9fr) minmax(0, 1.1fr);
  gap: 24px;
  align-items: center;
}

.hero-dark .contribution-strip {
  background: rgba(255, 255, 255, 0.04);
}

.section-chip {
  display: inline-block;
  padding: 0.5rem 0.85rem;
  border-radius: 999px;
  background: rgba(14, 165, 233, 0.12);
  color: #0369a1;
  font-size: 0.8rem;
  font-weight: 700;
  letter-spacing: 0.08em;
  text-transform: uppercase;
}

.contribution-copy h4 {
  font-family: "Space Grotesk", sans-serif;
  font-size: 1.7rem;
  line-height: 1.08;
  margin: 12px 0 10px;
}

.contribution-copy p {
  max-width: 420px;
  margin-bottom: 0;
  line-height: 1.75;
  color: #5f6f87;
}

.github-chart-wrapper {
  padding: 20px;
  background: rgba(255, 255, 255, 0.72);
  border-radius: 24px;
  border: 1px solid rgba(148, 163, 184, 0.14);
}

.github-chart {
  max-width: 100%;
  display: block;
  margin: 0 auto;
  border-radius: 16px;
  box-shadow: 0 18px 40px rgba(15, 23, 42, 0.08);
  transition: filter 0.3s ease;
}

.hero-dark .github-chart {
  filter: invert(1) hue-rotate(180deg);
}

@media only screen and (max-width: 991px) {
  .hero-shell {
    padding: 28px;
  }

  .hero-grid {
    min-height: auto;
  }

  .home-title {
    max-width: none;
  }

  .portrait-stage {
    max-width: 540px;
    margin-bottom: 18px;
  }

  .hero-insights {
    grid-template-columns: 1fr;
  }

  .contribution-strip {
    grid-template-columns: 1fr;
  }

  .floating-card-top {
    right: 0;
  }

  .floating-card-bottom {
    left: 0;
  }
}

@media only screen and (max-width: 580px) {
  .hero-shell {
    padding: 20px;
    border-radius: 28px;
  }

  .profile-image {
    height: 360px;
  }

  .hero-actions,
  .social-row {
    margin-left: -4px;
    margin-right: -4px;
  }

  .hero-btn {
    width: calc(100% - 8px);
    justify-content: center;
    margin-bottom: 10px;
  }

  .portrait-stage {
    padding: 12px 0 28px;
  }

  .portrait-card {
    padding: 14px;
    border-radius: 28px;
  }

  .floating-card {
    position: static;
    width: 100%;
    margin-top: 14px;
  }

  .portrait-footer {
    align-items: center;
  }

  .home-title {
    font-size: clamp(2.4rem, 10vw, 3.2rem);
  }

  .hero-subtitle {
    font-size: 1rem;
  }

  .contribution-strip {
    padding: 20px;
  }
}
</style>  
