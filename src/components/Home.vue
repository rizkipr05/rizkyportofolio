<template>
  <div :class="{ 'hero-dark': nightMode }" class="hero-section p-st">
    <div class="hero-shell" data-aos="fade" data-aos-once="true" data-aos-duration="1000">
      <div class="hero-backdrop"></div>
      <div class="container hero-content">
        <div class="row align-items-start hero-grid">
          <div
            class="col-xl-5 col-lg-6 col-md-12 col-sm-12 hero-visual"
            data-aos="fade-right"
            data-aos-duration="1200"
          >
            <div class="orb orb-one"></div>
            <div class="orb orb-two"></div>
            <div class="portrait-stage">
            <div class="portrait-card">
              <div class="lanyard-wrap" aria-hidden="true">
                <div class="lanyard-strap"></div>
                <div class="lanyard-clip"></div>
                <div class="lanyard-card">
                  <div class="lanyard-topbar">
                    <span class="lanyard-role">Developer ID</span>
                    <span class="lanyard-status">Active</span>
                  </div>
                  <div class="lanyard-body">
                    <img :src="picture" alt="" class="lanyard-avatar" />
                    <div class="lanyard-details">
                      <strong>{{ name }}</strong>
                      <span>Fullstack Engineer</span>
                      <small>IDRZK-2026</small>
                    </div>
                  </div>
                  <div class="lanyard-bottom">
                    <div class="lanyard-qr"></div>
                    <div class="lanyard-scan">
                      <span>Access level</span>
                      <strong>Product Build</strong>
                    </div>
                  </div>
                </div>
              </div>
              <div class="portrait-meta">
                <span class="meta-label">Available for freelance</span>
                <span class="meta-dot"></span>
                </div>
                <img :src="picture" class="profile-image" />
                <div class="portrait-footer">
                  <div>
                    <p class="portrait-name">{{ name }}</p>
                    <span class="portrait-role">Fullstack Developer</span>
                  </div>
                  <div class="portrait-badge">ID</div>
                </div>
              </div>
              <div class="floating-card floating-card-top">
                <strong>Fullstack Web Development</strong>
                <span>Robust backend, polished frontend</span>
              </div>
              <div class="floating-card floating-card-bottom">
                <strong>Based in Bandar Lampung</strong>
                <span>Open to remote collaboration</span>
              </div>
            </div>
          </div>
          <div
            class="col-xl-7 col-lg-6 col-md-12 col-sm-12 hero-copy"
            data-aos="fade-left"
            data-aos-duration="1200"
          >
            <div class="eyebrow">Fullstack Developer • Software Engineer • AI Enthusiast</div>
            <span class="home-title" :class="{ 'text-dark': !nightMode, 'text-light': nightMode }">
              Building complete digital products from backend logic to frontend experience.
            </span>
            <p class="hero-subtitle">
              I build fullstack web applications with a practical engineering mindset: scalable backend systems, reliable APIs, and clean user-facing interfaces.
            </p>
            <div class="hero-stack-strip">
              <span class="stack-token">Laravel</span>
              <span class="stack-token">React</span>
              <span class="stack-token">Vue</span>
              <span class="stack-token">Node.js</span>
              <span class="stack-token">PostgreSQL</span>
              <span class="stack-token">MySQL</span>
            </div>
            <div class="lead-copy" data-aos="fade-left" data-aos-delay="400">
              <p v-html="description"></p>
            </div>
            <div class="hero-insights" data-aos="fade-up" data-aos-delay="500">
              <div class="insight-card">
                <strong>3+ Years</strong>
                <span>Building websites, business systems, and fullstack products</span>
              </div>
              <div class="insight-card">
                <strong>Laravel • React • Vue</strong>
                <span>Comfortable handling frontend, backend, and integration flows</span>
              </div>
              <div class="insight-card">
                <strong>API + Interface</strong>
                <span>Not just visuals. I build systems that are usable and production-ready.</span>
              </div>
              <div class="insight-card">
                <strong>Final-Semester Builder</strong>
                <span>Strengthening real-world delivery through freelance and team projects.</span>
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

@keyframes swayCard {
  0% {
    transform: rotate(-6deg) translateY(0);
  }
  50% {
    transform: rotate(4deg) translateY(6px);
  }
  100% {
    transform: rotate(-6deg) translateY(0);
  }
}

.hero-section {
  position: relative;
  margin-top: -22px;
  padding: 0 0 92px;
  overflow: hidden;
}

.hero-shell {
  position: relative;
  width: 100%;
  padding: 28px 0 0;
  background:
    radial-gradient(circle at 8% 18%, rgba(56, 189, 248, 0.28), transparent 26%),
    radial-gradient(circle at 88% 12%, rgba(129, 140, 248, 0.22), transparent 24%),
    linear-gradient(135deg, rgba(244, 249, 255, 0.96), rgba(236, 242, 255, 0.92) 52%, rgba(241, 236, 255, 0.9));
  overflow: hidden;
}

.hero-dark .hero-shell {
  background:
    radial-gradient(circle at 10% 18%, rgba(34, 211, 238, 0.18), transparent 24%),
    radial-gradient(circle at 84% 12%, rgba(99, 102, 241, 0.2), transparent 22%),
    linear-gradient(180deg, rgba(6, 11, 23, 0.7), rgba(9, 16, 31, 0.3)),
    linear-gradient(180deg, #07111f 0%, #0a1628 55%, #08111f 100%);
}

.hero-content {
  position: relative;
  z-index: 1;
}

.hero-content::before {
  content: "";
  position: absolute;
  top: 54px;
  right: 24px;
  width: min(42vw, 520px);
  height: 520px;
  border-radius: 36px;
  background:
    linear-gradient(180deg, rgba(255, 255, 255, 0.34), rgba(255, 255, 255, 0.08)),
    radial-gradient(circle at top right, rgba(59, 130, 246, 0.12), transparent 52%);
  border: 1px solid rgba(148, 163, 184, 0.14);
  box-shadow: 0 30px 80px rgba(15, 23, 42, 0.07);
  transform: rotate(-4deg);
  pointer-events: none;
}

.hero-dark .hero-content::before {
  background:
    linear-gradient(180deg, rgba(15, 23, 42, 0.36), rgba(15, 23, 42, 0.08)),
    radial-gradient(circle at top right, rgba(59, 130, 246, 0.14), transparent 52%);
  border-color: rgba(125, 211, 252, 0.08);
  box-shadow: 0 30px 80px rgba(2, 8, 23, 0.28);
}

.hero-backdrop {
  position: absolute;
  inset: 0;
  background:
    radial-gradient(circle at 16% 24%, rgba(56, 189, 248, 0.14), transparent 22%),
    radial-gradient(circle at 86% 18%, rgba(99, 102, 241, 0.12), transparent 24%),
    radial-gradient(circle at 48% 84%, rgba(255, 255, 255, 0.46), transparent 28%);
  pointer-events: none;
}

.hero-grid {
  min-height: 700px;
  padding-top: 54px;
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
  padding: 28px 18px 36px;
}

.portrait-card {
  position: relative;
  padding: 118px 18px 18px;
  border-radius: 34px;
  background: linear-gradient(180deg, rgba(255, 255, 255, 0.92), rgba(241, 246, 255, 0.72));
  border: 1px solid rgba(148, 163, 184, 0.18);
  box-shadow: 0 34px 80px rgba(15, 23, 42, 0.16);
  overflow: hidden;
}

.lanyard-wrap {
  position: absolute;
  top: -18px;
  right: 18px;
  z-index: 3;
  transform-origin: top center;
  animation: swayCard 5.5s ease-in-out infinite;
}

.lanyard-strap {
  width: 12px;
  height: 68px;
  margin: 0 auto;
  border-radius: 999px;
  background:
    repeating-linear-gradient(
      135deg,
      rgba(255, 255, 255, 0.88) 0 8px,
      rgba(14, 165, 233, 0.94) 8px 16px,
      rgba(37, 99, 235, 0.82) 16px 24px
    );
  box-shadow: 0 0 0 5px rgba(14, 165, 233, 0.08);
}

.lanyard-clip {
  width: 24px;
  height: 24px;
  margin: -4px auto 0;
  border-radius: 999px;
  background: #e2e8f0;
  border: 3px solid rgba(255, 255, 255, 0.92);
  box-shadow: 0 10px 20px rgba(15, 23, 42, 0.12);
}

.lanyard-card {
  width: 228px;
  margin-top: 10px;
  padding: 0;
  border-radius: 24px;
  background: linear-gradient(180deg, rgba(255, 255, 255, 0.98), rgba(237, 242, 255, 0.9));
  border: 1px solid rgba(148, 163, 184, 0.18);
  box-shadow: 0 24px 44px rgba(15, 23, 42, 0.18);
  overflow: hidden;
  backdrop-filter: blur(14px);
}

.hero-dark .lanyard-card {
  background: linear-gradient(180deg, rgba(20, 33, 54, 0.96), rgba(10, 19, 34, 0.9));
  border-color: rgba(125, 211, 252, 0.12);
}

.lanyard-topbar {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 10px 12px;
  background: linear-gradient(135deg, #0ea5e9, #2563eb);
  color: white;
}

.lanyard-role {
  font-size: 0.66rem;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  font-weight: 700;
}

.lanyard-status {
  padding: 0.26rem 0.5rem;
  border-radius: 999px;
  background: rgba(255, 255, 255, 0.18);
  font-size: 0.62rem;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  font-weight: 700;
}

.lanyard-body {
  display: grid;
  grid-template-columns: 56px 1fr;
  gap: 12px;
  padding: 14px 14px 12px;
  align-items: center;
}

.lanyard-avatar {
  width: 56px;
  height: 68px;
  object-fit: cover;
  object-position: center top;
  border-radius: 14px;
  border: 2px solid rgba(255, 255, 255, 0.9);
  box-shadow: 0 12px 20px rgba(15, 23, 42, 0.12);
}

.lanyard-details {
  min-width: 0;
}

.lanyard-card strong {
  display: block;
  font-family: "Space Grotesk", sans-serif;
  font-size: 0.9rem;
  line-height: 1.3;
  color: #0f172a;
  margin-bottom: 4px;
}

.hero-dark .lanyard-card strong {
  color: #f8fbff;
}

.lanyard-details span,
.lanyard-details small {
  display: block;
  text-transform: uppercase;
  letter-spacing: 0.05em;
}

.lanyard-details span {
  color: #64748b;
  font-size: 0.62rem;
  font-weight: 700;
  margin-bottom: 4px;
}

.lanyard-details small {
  color: #94a3b8;
  font-size: 0.62rem;
}

.hero-dark .lanyard-details span,
.hero-dark .lanyard-details small {
  color: rgba(231, 238, 252, 0.68);
}

.lanyard-bottom {
  display: flex;
  align-items: center;
  gap: 12px;
  padding: 0 14px 14px;
}

.lanyard-qr {
  width: 48px;
  height: 48px;
  border-radius: 12px;
  background:
    linear-gradient(90deg, #0f172a 8px, transparent 8px) 0 0 / 16px 16px,
    linear-gradient(#0f172a 8px, transparent 8px) 0 0 / 16px 16px,
    linear-gradient(135deg, #0ea5e9, #2563eb);
  box-shadow: inset 0 0 0 6px rgba(255, 255, 255, 0.9);
}

.hero-dark .lanyard-qr {
  box-shadow: inset 0 0 0 6px rgba(15, 23, 42, 0.92);
}

.lanyard-scan span,
.lanyard-scan strong {
  display: block;
}

.lanyard-scan span {
  font-size: 0.62rem;
  letter-spacing: 0.06em;
  text-transform: uppercase;
  color: #64748b;
  margin-bottom: 4px;
}

.lanyard-scan strong {
  font-size: 0.76rem;
  color: #0f172a;
}

.hero-dark .lanyard-scan span {
  color: rgba(231, 238, 252, 0.68);
}

.hero-dark .lanyard-scan strong {
  color: #f8fbff;
}

.hero-dark .portrait-card {
  background: linear-gradient(180deg, rgba(18, 31, 52, 0.84), rgba(11, 20, 36, 0.76));
  border-color: rgba(125, 211, 252, 0.12);
  box-shadow: 0 28px 70px rgba(1, 6, 18, 0.45);
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

.hero-dark .meta-label,
.hero-dark .eyebrow,
.hero-dark .section-chip {
  background: rgba(56, 189, 248, 0.12);
  color: #7dd3fc;
  border: 1px solid rgba(125, 211, 252, 0.12);
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
  padding: 0.72rem 1.05rem;
  border-radius: 999px;
  background: rgba(14, 165, 233, 0.1);
  color: #0369a1;
  font-size: 0.78rem;
  font-weight: 700;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  margin-bottom: 24px;
  box-shadow: 0 18px 40px rgba(14, 165, 233, 0.08);
}

.home-title {
  display: block;
  font-size: clamp(3rem, 5.1vw, 5.6rem);
  line-height: 0.92;
  font-weight: 700;
  letter-spacing: -0.068em;
  max-width: 9.6ch;
  text-wrap: balance;
  animation: slideFadeIn 1s ease-out forwards;
  animation-delay: 0.3s;
  opacity: 0;
  will-change: opacity, transform;
}

.hero-subtitle {
  max-width: 620px;
  margin: 24px 0 0;
  font-size: 1.12rem;
  line-height: 1.9;
  color: #334155;
}

.hero-dark .hero-subtitle {
  color: rgba(231, 238, 252, 0.82);
}

.hero-stack-strip {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
  margin-top: 22px;
  max-width: 720px;
}

.stack-token {
  display: inline-flex;
  align-items: center;
  padding: 0.58rem 0.86rem;
  border-radius: 999px;
  background: rgba(255, 255, 255, 0.74);
  border: 1px solid rgba(148, 163, 184, 0.16);
  box-shadow: 0 14px 28px rgba(15, 23, 42, 0.06);
  color: #0f172a;
  font-size: 0.82rem;
  font-weight: 700;
}

.hero-dark .stack-token {
  background: rgba(15, 23, 42, 0.72);
  border-color: rgba(125, 211, 252, 0.12);
  color: #dbeafe;
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
  gap: 16px;
  margin: 34px 0;
}

.insight-card {
  display: flex;
  flex-direction: column;
  gap: 6px;
  min-height: 128px;
  padding: 20px 20px 18px;
  border-radius: 24px;
  background:
    linear-gradient(180deg, rgba(255, 255, 255, 0.78), rgba(245, 249, 255, 0.72));
  border: 1px solid rgba(148, 163, 184, 0.18);
  backdrop-filter: blur(8px);
  box-shadow: 0 16px 34px rgba(15, 23, 42, 0.08);
  transition: transform 0.28s ease, box-shadow 0.28s ease;
}

.insight-card:hover {
  transform: translateY(-4px);
  box-shadow: 0 24px 44px rgba(15, 23, 42, 0.12);
}

.hero-dark .insight-card {
  background: linear-gradient(180deg, rgba(15, 26, 44, 0.88), rgba(10, 18, 31, 0.74));
  border-color: rgba(125, 211, 252, 0.1);
  box-shadow: 0 18px 48px rgba(2, 8, 23, 0.32);
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

.hero-dark .portrait-role {
  color: rgba(231, 238, 252, 0.7);
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
  background: linear-gradient(180deg, rgba(255, 255, 255, 0.92), rgba(241, 246, 255, 0.82));
  border: 1px solid rgba(148, 163, 184, 0.18);
  box-shadow: 0 20px 50px rgba(15, 23, 42, 0.12);
  backdrop-filter: blur(12px);
}

.hero-dark .floating-card {
  background: linear-gradient(180deg, rgba(14, 24, 40, 0.88), rgba(9, 16, 29, 0.82));
  border-color: rgba(125, 211, 252, 0.12);
  box-shadow: 0 20px 60px rgba(0, 0, 0, 0.34);
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
  top: 18px;
  right: -8px;
}

.floating-card-bottom {
  left: -10px;
  bottom: 18px;
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
  margin: 18px -8px 0;
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
  background: rgba(15, 23, 42, 0.74);
  color: #7dd3fc;
  border-color: rgba(125, 211, 252, 0.14);
  box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.04);
}

.hero-dark .hero-btn.btn-primary {
  background: linear-gradient(135deg, #0284c7, #2563eb);
  color: white;
  box-shadow: 0 20px 40px rgba(37, 99, 235, 0.28);
}

.btn:focus {
  color: white;
  outline: none !important;
}

.contribution-strip {
  position: relative;
  z-index: 1;
  margin-top: 42px;
  padding: 28px 30px;
  border-radius: 30px;
  background: rgba(255, 255, 255, 0.58);
  border: 1px solid rgba(148, 163, 184, 0.18);
  display: grid;
  grid-template-columns: minmax(260px, 0.9fr) minmax(0, 1.1fr);
  gap: 24px;
  align-items: center;
}

.hero-dark .contribution-strip {
  background: linear-gradient(180deg, rgba(14, 24, 40, 0.84), rgba(9, 16, 29, 0.76));
  border-color: rgba(125, 211, 252, 0.1);
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

.hero-dark .github-chart-wrapper {
  background: rgba(8, 17, 31, 0.72);
  border-color: rgba(125, 211, 252, 0.08);
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
  .hero-grid {
    min-height: auto;
    padding-top: 28px;
  }

  .hero-content::before {
    display: none;
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
  .hero-section {
    margin-top: -14px;
    padding-top: 0;
    padding-bottom: 56px;
  }

  .hero-grid {
    padding-top: 12px;
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

  .lanyard-wrap {
    position: static;
    margin-bottom: 14px;
    animation: none;
  }

  .lanyard-strap,
  .lanyard-clip {
    display: none;
  }

  .lanyard-card {
    width: 100%;
    margin-top: 0;
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
