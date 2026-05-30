<template>
  <div id="app" :class="{ 'text-dark': !nightMode, 'text-light': nightMode }">
    <Navbar @scroll="scrollTo" @nightMode="switchMode" :nightMode="nightMode" />
    <div class="parent">
      <Home :nightMode="nightMode" />
      <About id="about" :nightMode="nightMode" />
      <Skills id="skills" :nightMode="nightMode" />
      <Certificate id="certificate" :nightMode="nightMode" />
      <Portfolio id="portfolio" :nightMode="nightMode" />
      <Galery id="galery" :nightMode="nightMode" />
      <Contact id="contact" :nightMode="nightMode" />
      <Footer :nightMode="nightMode" />
    </div>
  </div>
</template>

<script>
import Navbar from "./components/Navbar.vue";
import Home from "./components/Home";
import About from "./components/About";
import Skills from "./components/Skills";
import Certificate from "./components/Certificate.vue"; 
import Portfolio from "./components/Portfolio";
import Galery from "./components/Galery.vue"; 
import Contact from "./components/Contact";
import Footer from "./components/Footer";

import info from "../info";

export default {
  name: "App",
  components: {
    Navbar,
    Home,
    About,
    Skills,
    Certificate,
    Portfolio,
    Galery,
    Contact,
    Footer,
  },
  data() {
    return {
      nightMode: false,
      config: info.config,
    };
  },
  created() {
    if (this.config.use_cookies) {
      this.nightMode = this.$cookie.get("nightMode") === "true" ? true : false;
    }
  },
  mounted() {
    ["about", "contact", "skills", "portfolio"].forEach((l) => {
      if (window.location.href.includes(l)) {
        var elementPosition = document.getElementById(l).offsetTop;
        window.scrollTo({ top: elementPosition - 35, behavior: "smooth" });
      }
    });
  },
  methods: {
    switchMode(mode) {
      if (this.config.use_cookies) {
        this.$cookie.set("nightMode", mode);
      }
      this.nightMode = mode;
    },
    scrollTo(ele) {
      if (ele == "home") {
        this.$router.push(`/`).catch(()=>{});
        window.scrollTo({ top: -80, behavior: "smooth" });
      } else {
        var elementPosition = document.getElementById(ele).offsetTop;
        window.scrollTo({ top: elementPosition - 35, behavior: "smooth" });
        if (this.$router.history.current.path !== `/${ele}`)
          this.$router.push(`/${ele}`);
      }
    },
  },
};
</script>

<style>
:root {
  --bg-page: #f4f7fb;
  --bg-surface: rgba(255, 255, 255, 0.72);
  --bg-surface-strong: rgba(255, 255, 255, 0.92);
  --bg-dark: #08111f;
  --bg-dark-surface: rgba(10, 18, 33, 0.82);
  --text-primary: #0c1729;
  --text-secondary: #5f6f87;
  --accent: #0ea5e9;
  --accent-strong: #2563eb;
  --accent-soft: rgba(14, 165, 233, 0.14);
  --border-soft: rgba(130, 154, 186, 0.22);
  --shadow-soft: 0 24px 80px rgba(11, 27, 52, 0.12);
  --shadow-strong: 0 30px 80px rgba(7, 15, 31, 0.28);
  --radius-xl: 30px;
  --radius-lg: 22px;
}

html {
  scroll-behavior: smooth;
}

body {
  background:
    radial-gradient(circle at top left, rgba(14, 165, 233, 0.18), transparent 28%),
    radial-gradient(circle at top right, rgba(37, 99, 235, 0.16), transparent 24%),
    linear-gradient(180deg, #f8fbff 0%, #eef4fb 100%);
  color: var(--text-primary);
}

#app {
  font-family: "Outfit", sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: var(--text-primary);
  width: 100%;
  min-height: 100vh;
}

@media screen and (max-width: 580px) {
  #app {
    width: 100%;
  }
}

.parent {
  margin-top: 32px;
  padding-top: 56px;
  position: relative;
  overflow: hidden;
}

.pgray {
  color: var(--text-secondary);
}

.pblue {
  color: var(--accent);
}

.bg-dark2 {
  background: linear-gradient(180deg, rgba(8, 17, 31, 0.98), rgba(13, 24, 42, 0.98)) !important;
}

.text-light {
  color: #e7eefc !important;
}

.text-dark {
  color: var(--text-primary) !important;
}

.p-st {
  transition: all 0.5s !important;
}

.container {
  max-width: 1180px;
}

.title,
.title1,
.title2,
.title3,
.home-title,
.section-title {
  font-family: "Space Grotesk", sans-serif;
  letter-spacing: -0.03em;
}

.badge {
  border-radius: 999px;
}

hr {
  border-top: 1px solid rgba(143, 161, 183, 0.2);
}

/* To set scrollbar width */
::-webkit-scrollbar {
  width: 5px;
}

/* Track */
::-webkit-scrollbar-track {
  background: #f1f1f1;
  border-radius: 9px;
  border: 2px solid white; /* Use your background color instead of White */
  background-clip: content-box;
}

/* Handle */
::-webkit-scrollbar-thumb {
  background: #AEAEAE;
  border-radius: 9px;
}

/* Handle on hover */
::-webkit-scrollbar-thumb:hover {
  background: #949494;
}

.tooltip {
  display: block !important;
  z-index: 10000;
}

.tooltip .tooltip-inner {
  background: #0f172a;
  color: white;
  border-radius: 10px;
  font-size: 10px;
}

.tooltip .tooltip-arrow {
  width: 0;
  height: 0;
  border-style: solid;
  position: absolute;
  margin: 5px;
  border-color: #0f172a;
  z-index: 1;
}

.tooltip[x-placement^="top"] {
  margin-bottom: 5px;
}

.tooltip[x-placement^="top"] .tooltip-arrow {
  border-width: 5px 5px 0 5px;
  border-left-color: transparent !important;
  border-right-color: transparent !important;
  border-bottom-color: transparent !important;
  bottom: -5px;
  left: calc(50% - 5px);
  margin-top: 0;
  margin-bottom: 0;
}

.tooltip[x-placement^="bottom"] {
  margin-top: 10px;
}

.tooltip[x-placement^="bottom"] .tooltip-arrow {
  border-width: 0 5px 5px 5px;
  border-left-color: transparent !important;
  border-right-color: transparent !important;
  border-top-color: transparent !important;
  top: -5px;
  left: calc(50% - 5px);
  margin-top: 0;
  margin-bottom: 0;
}

.tooltip[x-placement^="right"] {
  margin-left: 5px;
}

.tooltip[x-placement^="right"] .tooltip-arrow {
  border-width: 5px 5px 5px 0;
  border-left-color: transparent !important;
  border-top-color: transparent !important;
  border-bottom-color: transparent !important;
  left: -5px;
  top: calc(50% - 5px);
  margin-left: 0;
  margin-right: 0;
}

.tooltip[x-placement^="left"] {
  margin-right: 5px;
}

.tooltip[x-placement^="left"] .tooltip-arrow {
  border-width: 5px 0 5px 5px;
  border-top-color: transparent !important;
  border-right-color: transparent !important;
  border-bottom-color: transparent !important;
  right: -5px;
  top: calc(50% - 5px);
  margin-left: 0;
  margin-right: 0;
}

.tooltip.popover .popover-inner {
  background: #f9f9f9;
  color: black;
  padding: 24px;
  border-radius: 5px;
  box-shadow: 0 5px 30px rgba(black, 0.1);
}

.tooltip.popover .popover-arrow {
  border-color: #f9f9f9;
}

.tooltip[aria-hidden="true"] {
  visibility: hidden;
  opacity: 0;
  transition: opacity 0.5s, visibility 0.5s;
}

.tooltip[aria-hidden="false"] {
  visibility: visible;
  opacity: 1;
  transition: opacity 0.5s;
}
</style>
