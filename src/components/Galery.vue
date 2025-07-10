<template>
  <div :class="{ 'bg-white': !nightMode, 'bg-dark': nightMode }" class="p-st">
    <div class="container py-4">
      <!-- Header -->
      <div class="text-center" data-aos="fade" data-aos-once="true" data-aos-duration="1000">
        <span class="title text-center" :class="{ 'text-dark': !nightMode, 'text-light': nightMode }">
          Gallery
        </span>
      </div>
      <hr width="50%" :class="{ pgray: !nightMode, 'bg-secondary': nightMode }" />
      <div class="text-center mt-3 mb-4">
        <p class="description" :class="{ 'text-dark': !nightMode, 'text-light': nightMode }">
          This is a gallery showcasing my recent activities. Feel free to explore and take a look!
        </p>
      </div>

      <!-- Gallery Slider -->
      <div class="slider-container">
        <div class="slider-wrapper" :style="{ transform: `translateX(-${currentSlide * 100}%)` }">
          <div class="slide" v-for="(slide, index) in slides" :key="index">
            <img :src="slide.image" :alt="slide.alt" class="slide-image" />
          </div>
        </div>

        <!-- Navigation Arrows -->
        <button class="nav-arrow prev" :class="{ 'nav-light': !nightMode, 'nav-dark': nightMode }" @click="prevSlide">
          <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
            <polyline points="15,18 9,12 15,6"></polyline>
          </svg>
        </button>
        
        <button class="nav-arrow next" :class="{ 'nav-light': !nightMode, 'nav-dark': nightMode }" @click="nextSlide">
          <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
            <polyline points="9,18 15,12 9,6"></polyline>
          </svg>
        </button>

        <!-- Auto-play Control -->
        <button class="control-btn" :class="{ 'nav-light': !nightMode, 'nav-dark': nightMode }" @click="toggleAutoplay">
          <svg v-if="isAutoPlaying" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
            <rect x="6" y="4" width="4" height="16"></rect>
            <rect x="14" y="4" width="4" height="16"></rect>
          </svg>
          <svg v-else width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
            <polygon points="5,3 19,12 5,21"></polygon>
          </svg>
        </button>

        <!-- Pagination Dots -->
        <div class="pagination">
          <button 
            v-for="(slide, index) in slides" 
            :key="index"
            class="pagination-dot"
            :class="{ 
              'dot-active-light': currentSlide === index && !nightMode,
              'dot-active-dark': currentSlide === index && nightMode,
              'dot-inactive-light': currentSlide !== index && !nightMode,
              'dot-inactive-dark': currentSlide !== index && nightMode
            }"
            @click="goToSlide(index)"
          ></button>
        </div>
      </div>

      <!-- Image Counter -->
      <div class="text-center mt-3">
        <span class="counter" :class="{ 'text-dark': !nightMode, 'text-light': nightMode }">
          {{ currentSlide + 1 }} / {{ slides.length }}
        </span>
      </div>
    </div>
  </div>
</template>

<script>
import AOS from "aos";
import "aos/dist/aos.css";

export default {
  name: "Gallery",
  props: {
    nightMode: Boolean,
  },
  data() {
    return {
      currentSlide: 0,
      isAutoPlaying: true,
      autoplayInterval: null,
      slides: [
        {
          image: require("@/assets/foto/8.jpg"),
          alt: "Gallery Image 1"
        },
        {
          image: require("@/assets/foto/2.jpg"), 
          alt: "Gallery Image 2"
        },
        {
          image: require("@/assets/foto/6.jpg"),
          alt: "Gallery Image 3"
        },
        {
          image: require("@/assets/foto/4.jpg"),
          alt: "Gallery Image 4"
        },
        {
          image: require("@/assets/foto/5.jpg"),
          alt: "Gallery Image 5"
        }
      ]
    };
  },
  mounted() {
    AOS.init();
    this.startAutoplay();
  },
  beforeUnmount() {
    this.stopAutoplay();
  },
  methods: {
    nextSlide() {
      this.currentSlide = (this.currentSlide + 1) % this.slides.length;
    },
    prevSlide() {
      this.currentSlide = (this.currentSlide - 1 + this.slides.length) % this.slides.length;
    },
    goToSlide(index) {
      this.currentSlide = index;
    },
    startAutoplay() {
      if (this.isAutoPlaying) {
        this.autoplayInterval = setInterval(() => {
          this.nextSlide();
        }, 4000);
      }
    },
    stopAutoplay() {
      if (this.autoplayInterval) {
        clearInterval(this.autoplayInterval);
        this.autoplayInterval = null;
      }
    },
    toggleAutoplay() {
      this.isAutoPlaying = !this.isAutoPlaying;
      if (this.isAutoPlaying) {
        this.startAutoplay();
      } else {
        this.stopAutoplay();
      }
    }
  },
  watch: {
    currentSlide() {
      if (this.isAutoPlaying) {
        this.stopAutoplay();
        this.startAutoplay();
      }
    }
  }
};
</script>

<style scoped>
.title {
  font-size: 30px;
  font-weight: 500;
}

.text-dark {
  color: #111;
}

.text-light {
  color: #fff;
}

.bg-dark {
  background-color: #111;
}

.pgray {
  border-color: #ccc;
}

.bg-secondary {
  border-color: #666;
}

.p-st {
  padding: 2rem 1rem;
}

.counter {
  font-size: 14px;
  font-weight: 400;
}

.description {
  font-size: 16px;
  font-weight: 400;
  margin: 0;
  opacity: 0.8;
}

/* Slider Styles */
.slider-container {
  position: relative;
  width: 100%;
  height: 400px;
  overflow: hidden;
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

.slider-wrapper {
  display: flex;
  width: 100%;
  height: 100%;
  transition: transform 0.7s ease-in-out;
}

.slide {
  flex: 0 0 100%;
  height: 100%;
}

.slide-image {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.3s ease;
}

.slide-image:hover {
  transform: scale(1.05);
}

/* Navigation Arrows */
.nav-arrow {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  border: none;
  width: 40px;
  height: 40px;
  border-radius: 50%;
  cursor: pointer;
  transition: all 0.3s ease;
  z-index: 10;
  display: flex;
  align-items: center;
  justify-content: center;
}

.nav-arrow.prev {
  left: 15px;
}

.nav-arrow.next {
  right: 15px;
}

/* Navigation Light Mode */
.nav-light {
  background-color: #f9f9f9;
  color: #111;
  border: 1px solid #ccc;
}

.nav-light:hover {
  background-color: #e9e9e9;
  transform: translateY(-50%) scale(1.1);
}

/* Navigation Dark Mode */
.nav-dark {
  background-color: #111;
  color: #00f0ff;
  border: 1px solid #00f0ff;
}

.nav-dark:hover {
  background-color: #222;
  box-shadow: 0 0 12px #00f0ff;
  transform: translateY(-50%) scale(1.1);
}

/* Control Button */
.control-btn {
  position: absolute;
  top: 15px;
  right: 15px;
  border: none;
  width: 36px;
  height: 36px;
  border-radius: 50%;
  cursor: pointer;
  transition: all 0.3s ease;
  z-index: 10;
  display: flex;
  align-items: center;
  justify-content: center;
}

/* Pagination Dots */
.pagination {
  position: absolute;
  bottom: 15px;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  gap: 8px;
  z-index: 10;
}

.pagination-dot {
  width: 10px;
  height: 10px;
  border-radius: 50%;
  border: none;
  cursor: pointer;
  transition: all 0.3s ease;
}

/* Pagination Light Mode */
.dot-active-light {
  background-color: #111;
  transform: scale(1.2);
}

.dot-inactive-light {
  background-color: #ccc;
}

.dot-inactive-light:hover {
  background-color: #999;
}

/* Pagination Dark Mode */
.dot-active-dark {
  background-color: #00f0ff;
  transform: scale(1.2);
  box-shadow: 0 0 8px #00f0ff;
}

.dot-inactive-dark {
  background-color: #666;
}

.dot-inactive-dark:hover {
  background-color: #888;
}

/* Responsive Design */
@media (max-width: 768px) {
  .slider-container {
    height: 300px;
  }
  
  .nav-arrow {
    width: 35px;
    height: 35px;
  }
  
  .nav-arrow.prev {
    left: 10px;
  }
  
  .nav-arrow.next {
    right: 10px;
  }
  
  .control-btn {
    width: 32px;
    height: 32px;
    top: 10px;
    right: 10px;
  }
}

@media (max-width: 480px) {
  .slider-container {
    height: 250px;
  }
  
  .title {
    font-size: 24px;
  }
  
  .p-st {
    padding: 1rem 0.5rem;
  }
}
</style>