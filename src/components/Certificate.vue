<template>
    <section id="certificate" :class="{ 'bg-dark2': nightMode }">
      <div class="container p-st">
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
    font-size: 30px;
    font-weight: bold;
    text-align: center;
    color: #ccc;
    margin-top: 60px;     /* ✅ Tambahan */
    margin-bottom: 30px;
    border-bottom: 1px solid #6b6b6b;
    display: inline-block;
    padding-bottom: 8px;
    width: 100%;
    }

  
  .cert-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
    gap: 24px;
  }
  
  .cert-card {
    background-color: white;
    border-radius: 12px;
    overflow: hidden;
    box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
    transition: transform 0.3s ease;
  }
  
  .cert-card:hover {
    transform: translateY(-5px);
  }
  
  .cert-card img {
    width: 100%;
    height: auto;
    display: block;
  }
  
  .bg-dark2 .cert-card {
    background-color: #2f2f2f;
  }

  .text-dark {
  color: #111;
  }

</style>
  