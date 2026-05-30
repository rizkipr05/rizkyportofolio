<template>
    <section id="certificate" class="certificate-section" :class="{ 'bg-dark2': nightMode }">
      <div class="container p-st py-5">
        <div class="text-center">
          <span class="section-kicker">Proof of work</span>
        </div>
        <h2
        class="section-title"
        :class="{ 'text-light': nightMode, 'text-dark': !nightMode }"
        >
        Certificates
        </h2>

        <div class="cert-grid">
          <div
            class="cert-card"
            v-for="(cert, index) in certificates"
            :key="index"
          >
            <img :src="cert.image" :alt="cert.name" />
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
    .section-title {
    font-size: 2.4rem;
    font-weight: 700;
    text-align: center;
    color: #ccc;
    margin-top: 12px;
    margin-bottom: 36px;
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

  .cert-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
    gap: 24px;
  }
  
  .cert-card {
    background-color: rgba(255, 255, 255, 0.72);
    border-radius: 24px;
    overflow: hidden;
    border: 1px solid rgba(148, 163, 184, 0.18);
    box-shadow: 0 22px 55px rgba(15, 23, 42, 0.08);
    transition: transform 0.3s ease, box-shadow 0.3s ease;
  }
  
  .cert-card:hover {
    transform: translateY(-8px);
    box-shadow: 0 28px 60px rgba(15, 23, 42, 0.14);
  }
  
  .cert-card img {
    width: 100%;
    height: auto;
    display: block;
  }
  
  .bg-dark2 .cert-card {
    background-color: rgba(255, 255, 255, 0.04);
    border-color: rgba(148, 163, 184, 0.12);
  }

  .text-dark {
  color: #111;
  }

</style>
  
