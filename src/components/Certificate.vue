<template>
  <section id="certificate" class="certificate-section" :class="{ 'bg-dark2': nightMode }">
    <div class="container cert-shell p-st py-5">
      <div class="cert-head">
        <div class="cert-copy">
          <span class="section-kicker">Proof of work</span>
          <h2
            class="section-title"
            :class="{ 'text-light': nightMode, 'text-dark': !nightMode }"
          >
            Certifications and learning milestones that support my practice.
          </h2>
          <p class="cert-description">
            These certificates reflect continuous learning across design, development, and technical growth.
          </p>
        </div>

        <div class="cert-panel">
          <div class="cert-stat">
            <strong>{{ certificates.length }}+</strong>
            <span>learning records and certificates collected</span>
          </div>
        </div>
      </div>

      <div class="cert-grid">
        <div
          class="cert-card"
          v-for="(cert, index) in certificates"
          :key="index"
          :data-aos="'fade-up'"
          :data-aos-delay="index * 60"
        >
          <div class="cert-media">
            <img :src="cert.image" :alt="cert.name" />
          </div>
          <div class="cert-footer">
            <span class="cert-tag">Certificate</span>
            <strong>{{ cert.name }}</strong>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import info from "../../info";

export default {
  name: "Certificate",
  props: {
    nightMode: Boolean,
  },
  data() {
    return {
      certificates: info.certificates,
    };
  },
};
</script>

<style scoped>
.certificate-section {
  position: relative;
  overflow: hidden;
  padding: 36px 0 88px;
}

.certificate-section::before {
  content: "";
  position: absolute;
  left: -7%;
  top: 16%;
  width: 280px;
  height: 280px;
  border-radius: 50%;
  background: radial-gradient(circle, rgba(56, 189, 248, 0.18), transparent 72%);
  pointer-events: none;
}

.certificate-section::after {
  content: "";
  position: absolute;
  right: -5%;
  bottom: 10%;
  width: 340px;
  height: 340px;
  border-radius: 50%;
  background: radial-gradient(circle, rgba(129, 140, 248, 0.14), transparent 72%);
  pointer-events: none;
}

.cert-shell {
  position: relative;
  z-index: 1;
}

.cert-head {
  display: grid;
  grid-template-columns: minmax(0, 1.1fr) minmax(260px, 0.9fr);
  gap: 28px;
  align-items: end;
  margin-bottom: 36px;
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

.section-title {
  margin: 18px 0 14px;
  font-size: clamp(2.4rem, 4vw, 4rem);
  line-height: 1;
  font-weight: 700;
  max-width: 12ch;
}

.cert-description {
  max-width: 620px;
  margin: 0;
  line-height: 1.85;
  color: #5f6f87;
}

.cert-panel {
  padding: 24px;
  border-radius: 30px;
  background: linear-gradient(180deg, rgba(255, 255, 255, 0.84), rgba(244, 247, 255, 0.74));
  border: 1px solid rgba(148, 163, 184, 0.18);
  box-shadow: 0 24px 56px rgba(15, 23, 42, 0.08);
}

.bg-dark2 .cert-panel {
  background: linear-gradient(180deg, rgba(14, 24, 40, 0.92), rgba(9, 16, 29, 0.86));
  border-color: rgba(125, 211, 252, 0.1);
  box-shadow: 0 24px 56px rgba(2, 8, 23, 0.24);
}

.cert-stat strong {
  display: block;
  font-family: "Space Grotesk", sans-serif;
  font-size: 2.4rem;
  line-height: 1;
  margin-bottom: 8px;
}

.cert-stat span {
  color: #5f6f87;
  line-height: 1.8;
}

.bg-dark2 .cert-stat span {
  color: rgba(231, 238, 252, 0.7);
}

.cert-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
  gap: 24px;
}

.cert-card {
  overflow: hidden;
  border-radius: 28px;
  background: linear-gradient(180deg, rgba(255, 255, 255, 0.82), rgba(245, 248, 255, 0.76));
  border: 1px solid rgba(148, 163, 184, 0.18);
  box-shadow: 0 22px 55px rgba(15, 23, 42, 0.08);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.cert-card:hover {
  transform: translateY(-8px);
  box-shadow: 0 30px 64px rgba(15, 23, 42, 0.14);
}

.cert-media {
  padding: 16px;
}

.cert-card img {
  width: 100%;
  display: block;
  border-radius: 20px;
}

.cert-footer {
  padding: 0 18px 18px;
}

.cert-tag {
  display: inline-flex;
  align-items: center;
  margin-bottom: 10px;
  padding: 0.42rem 0.72rem;
  border-radius: 999px;
  background: rgba(14, 165, 233, 0.1);
  color: #0369a1;
  font-size: 0.74rem;
  font-weight: 700;
  letter-spacing: 0.06em;
  text-transform: uppercase;
}

.cert-footer strong {
  display: block;
  font-family: "Space Grotesk", sans-serif;
  font-size: 1rem;
  color: #0f172a;
}

.bg-dark2 .cert-card {
  background: linear-gradient(180deg, rgba(14, 24, 40, 0.92), rgba(9, 16, 29, 0.86));
  border-color: rgba(125, 211, 252, 0.1);
  box-shadow: 0 24px 56px rgba(2, 8, 23, 0.24);
}

.bg-dark2 .cert-tag {
  background: rgba(56, 189, 248, 0.12);
  color: #7dd3fc;
}

.bg-dark2 .cert-footer strong {
  color: #f8fbff;
}

@media only screen and (max-width: 991px) {
  .cert-head {
    grid-template-columns: 1fr;
  }

  .section-title {
    max-width: none;
  }
}

@media only screen and (max-width: 580px) {
  .certificate-section {
    padding: 24px 0 60px;
  }
}
</style>
