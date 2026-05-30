<template>
  <div>
    <nav
      class="navbar navbar-expand-lg fixed-top p-st modern-navbar"
      :class="{
        'navbar-blur': navbarConfig.blur,
        'bg-dark2': nightMode,
        'is-dark': nightMode,
      }"
    >
      <div class="container">
        <a
          class="navbar-brand"
          href="/"
          @click.prevent="$emit('scroll', 'home')"
        >
          <Logo :nightMode="nightMode" />
        </a>
        <button
          class="navbar-toggler"
          type="button"
          data-toggle="collapse"
          data-target="#navbarSupportedContent"
          aria-controls="navbarSupportedContent"
          aria-expanded="false"
          aria-label="Toggle navigation"
        >
          <span style="color: gray; font-size: 23px;"
            ><i class="fas fa-bars"></i>
            </span>
        </button>

        <div class="collapse navbar-collapse" id="navbarSupportedContent">
          <ul class="navbar-nav ml-auto align-items-lg-center">
            <li class="nav-item mx-2">
              <a
                class="nav-link nav-pill"
                href="/about"
                @click.prevent="$emit('scroll', 'about')"
                :class="{ 'text-light': nightMode }"
                >About</a
              >
            </li>
            <li class="nav-item mx-2">
              <a
                class="nav-link nav-pill"
                href="/skills"
                @click.prevent="$emit('scroll', 'skills')"
                :class="{ 'text-light': nightMode }"
                >Skills</a
              >
            </li>
            <li class="nav-item mx-2">
            <a
              class="nav-link nav-pill"
              href="/certificate"
              @click.prevent="$emit('scroll', 'certificate')"
              :class="{ 'text-light': nightMode }"
              >Certificates</a
            >
          </li>
            <li class="nav-item mx-2 ">
              <a
                class="nav-link nav-pill"
                href="/portfolio"
                @click.prevent="$emit('scroll', 'portfolio')"
                :class="{ 'text-light': nightMode }"
                >Portfolio</a
              >
            </li>
            <li class="nav-item mx-2">
            <a
              class="nav-link nav-pill"
              href="/galery"
              @click.prevent="$emit('scroll', 'galery')"
              :class="{ 'text-light': nightMode }"
              >Galery</a
            >
          </li>
            <li class="nav-item mx-2">
              <a
                class="nav-link nav-pill"
                href="/contact"
                @click.prevent="$emit('scroll', 'contact')"
                :class="{ 'text-light': nightMode }"
                >Contact</a
              >
            </li>
            <li class="nav-item ml-2">
              <a
                class="nav-link mode-pill"
                href="#"
                @click.prevent="switchMode"
                :class="{ 'text-light': nightMode }"
                ><i
                  :class="{
                    'fas fa-moon': nightMode,
                    'far fa-moon': !nightMode,
                  }"
                  v-tooltip.bottom="nightMode ? 'Light Mode' : 'Night Mode'"
                ></i
              ></a>
            </li>
          </ul>
        </div>
      </div>
    </nav>
  </div>
</template>

<script>
import Logo from "./helpers/Logo";
import info from "../../info";

export default {
  name: "Navbar",
  props: {
    nightMode: {
      type: Boolean,
    },
  },
  data() {
    return {
      navbarConfig: info.config.navbar,
      localNightMode: this.nightMode,
    };
  },
  components: {
    Logo,
  },
  methods: {
    switchMode() {
      this.localNightMode = !this.localNightMode;
      this.$emit("nightMode", this.localNightMode);
    },
  },
};
</script>

<style scoped>
.nav-link {
  font-weight: 500;
  color: #0f172a;
}

.modern-navbar {
  background: rgba(255, 255, 255, 0.72);
  backdrop-filter: blur(18px);
  border-bottom: 1px solid rgba(148, 163, 184, 0.14);
  box-shadow: 0 14px 40px rgba(15, 23, 42, 0.06);
}

.modern-navbar.is-dark {
  background: rgba(8, 17, 31, 0.72);
  box-shadow: 0 14px 40px rgba(0, 0, 0, 0.22);
}

.nav-pill {
  border-radius: 999px;
  padding: 0.65rem 1rem !important;
  transition: all 0.25s ease;
}

.nav-pill:hover,
.mode-pill:hover {
  background: rgba(14, 165, 233, 0.12);
  color: #0369a1 !important;
}

button {
  border: none;
  outline: none;
}

button:hover {
  border: none;
  outline: none;
}

nav {
  position: fixed !important;
}

.navbar-blur {
  background-color: #ffffff7e;
  backdrop-filter: blur(12px);
}

.mode-pill {
  width: 42px;
  height: 42px;
  padding: 0 !important;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  border-radius: 999px;
  border: 1px solid rgba(148, 163, 184, 0.2);
  margin-left: 8px;
}

@media screen and (max-width: 991px) {
  .navbar-collapse {
    margin-top: 16px;
    padding: 18px;
    border-radius: 22px;
    background: rgba(255, 255, 255, 0.9);
    border: 1px solid rgba(148, 163, 184, 0.18);
  }

  .is-dark .navbar-collapse {
    background: rgba(8, 17, 31, 0.94);
  }

  .mode-pill {
    margin-left: 0;
    margin-top: 12px;
  }
}
</style>
