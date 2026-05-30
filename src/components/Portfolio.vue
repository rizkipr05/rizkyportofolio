<template>
  <div
    class="py-5 p-st portfolio-section"
    :class="{
      'bg-light': !nightMode,
      'bg-dark2': nightMode,
      'text-light': nightMode,
    }"
  >
    <div class="container">
      <div
        class="text-center section-head"
        data-aos="fade"
        data-aos-once="true"
        data-aos-duration="1000"
      >
        <span class="section-kicker">Selected work</span>
        <span
          class="title text-center d-block mt-2"
          :class="{ pgray: !nightMode, 'text-light': nightMode }"
          >Portfolio</span
        >
      </div>
      <hr
        width="50%"
        :class="{ pgray: !nightMode, 'bg-secondary': nightMode }"
      />

      <vue-tabs :activeTextColor="!nightMode ? '#535A5E' : '#dfdfdf'">
      <v-tab title="design">
          <div class="row">
            <div
              v-for="(design, idx) in desgin_info"
              :key="idx"
              :class="{ 'mt-4': idx === 0 ? true : true }"
              class="col-xl-6 col-bg-6 col-md-12 col-sm-12"
              style="position: relative;"
            >
              <vueper-slides
                :dragging-distance="50"
                fixed-height="300px"
                :bullets="false"
                slide-content-outside="bottom"
                style="position: aboslute"
                  @click.prevent="showDesignModalFn(design)"

              >
                <vueper-slide
                  v-for="(slide, i) in design.pictures"
                  :key="i"
                  :image="slide.img"
                />
              </vueper-slides>
              <div
                style="width: 100%; display: flex; justify-content: space-between"
                class="mt-2"
              >
                <div>
                  <div class="title2" style="font-weight: 500;">{{ design.title }}</div>
                  <span
                    class="badge mr-2 mb-2"
                    v-for="tech in design.technologies"
                    :key="tech"
                    :class="{ 'bg-dark4': nightMode }"
                    >{{ tech }}</span
                  >
                  •
                  <span class="date ml-1">{{design.date}}</span>
                </div>

                <button
                  style="height: 31px; margin-top: 5px;"
                  class="btn-sm btn btn-outline-secondary no-outline"
                  @click.prevent="showDesignModalFn(design)"
                >
                  read more
                </button>
              </div>
            </div>
          </div>
          <br />
        </v-tab>
        <v-tab title="development">
          <br />
          <div class="row">
            <div
              class="col-xl-4 col-bg-4 col-md-6 col-sm-12"
              v-for="(portfolio, idx) in portfolio_info"
              :key="portfolio.name"
            >
              <Card
                :style="{ 'transition-delay': (idx % 3) / 4.2 + 's' }"
                :portfolio="portfolio"
                @show="showModalFn"
                data-aos="fade-up"
                :nightMode="nightMode"
                data-aos-offset="100"
                data-aos-delay="10"
                data-aos-duration="500"
                data-aos-easing="ease-in-out"
                data-aos-mirror="true"
                data-aos-once="true"
              />
            </div>
          </div>
          <div class="text-center py-3" v-if="showBtn !== 'show less'">
            <button class="btn" @click.prevent="showMore">{{ showBtn }}</button>
          </div>
        </v-tab>
      </vue-tabs>
    </div>
    <transition name="modal">
      <Modal
        :showModal="showModal"
        @close="closeModal"
        v-if="showModal"
        :portfolio="modal_info"
        :nightMode="nightMode"
      />
    </transition>
    <transition name="modal">
      <DesignModal
        :showModal="showDesignModal"
        @close="closeModal"
        v-if="showDesignModal"
        :portfolio="design_modal_info"
        :nightMode="nightMode"
      />
    </transition>
  </div>
</template>

<script>
import Card from "./helpers/Card";
import Modal from "./helpers/Modal";
import DesignModal from "./helpers/DesignModal";
import Carousel from "./helpers/Carousel";
import info from "../../info";

import { VueTabs, VTab } from "vue-nav-tabs";
import "vue-nav-tabs/themes/vue-tabs.css";

import { VueperSlides, VueperSlide } from "vueperslides";
import "vueperslides/dist/vueperslides.css";

export default {
  name: "Portfolio",
  components: {
    Card,
    Modal,
    VueTabs,
    VTab,
    VueperSlides,
    VueperSlide,
    DesignModal,
  },
  props: {
    nightMode: {
      type: Boolean,
    },
  },
  data() {
    return {
      all_info: info.portfolio,
      desgin_info: info.portfolio_design,
      portfolio_info: [],
      showModal: false,
      showDesignModal: false,
      modal_info: {},
      design_modal_info: {},
      number: 3,
      showBtn: "show more",
      shower: 0,
      data: [
        '<div class="example-slide">Slide 1</div>',
        '<div class="example-slide">Slide 2</div>',
        '<div class="example-slide">Slide 3</div>',
      ],
    };
  },
  created() {
    for (var i = 0; i < this.number; i++) {
      this.portfolio_info.push(this.all_info[i]);
    }
  },
  watch: {
    number() {
      this.portfolio_info = [];
      for (var i = 0; i < this.number; i++) {
        this.portfolio_info.push(this.all_info[i]);
      }
    },
  },
  methods: {
    next() {
      this.$refs.flickity.next();
    },

    previous() {
      this.$refs.flickity.previous();
    },
    closeModal() {
      this.showModal = false;
      this.showDesignModal = false;
      document.getElementsByTagName("body")[0].classList.remove("modal-open");
    },
    showModalFn(portfolio) {
      this.modal_info = portfolio;
      this.showModal = true;
    },
    showDesignModalFn(design_portfolio) {
      this.design_modal_info = design_portfolio;
      this.showDesignModal = true;
    },
    showMore() {
      if (this.number != this.all_info.length) {
        this.number += 3;

        window.scrollBy({
          top: document.getElementsByClassName("smcard")[0].clientHeight,
          behavior: "smooth",
        });

        if (this.number > this.all_info.length)
          this.number = this.all_info.length;
      }

      if (this.number == this.all_info.length && this.shower == 0) {
        this.shower = 1;
        this.showBtn = "show less";
      } else if (this.number == this.all_info.length && this.shower == 1) {
        var elementPosition = document.getElementById("portfolio").offsetTop;
        window.scrollTo({ top: elementPosition + 5, behavior: "smooth" });
        this.shower = 0;
        this.number = 3;
        this.showBtn = "show more";
      }
    },
  },
};
</script>

<style scoped>
.title {
  font-size: 2.4rem;
  font-weight: 700;
}

.title1 {
  font-size: 24px;
  font-weight: 400;
}

.title2 {
  font-size: 1.2rem;
  font-weight: 600;
}

.title3 {
  font-size: 16px;
  font-weight: 400;
}

.section-head {
  margin-bottom: 18px;
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

.modal-enter {
  opacity: 0;
}

.modal-leave-active {
  opacity: 0;
}

.modal-enter .modal-container,
.modal-leave-active .modal-container {
  -webkit-transform: scale(1.1);
  transform: scale(1.1);
}

/deep/ .portfolio-section .vue-tabs {
  margin-top: 26px;
}

/deep/ .portfolio-section .nav-tabs {
  border: none;
  justify-content: center;
  gap: 12px;
}

/deep/ .portfolio-section .nav-tabs > li > a {
  border: 1px solid rgba(148, 163, 184, 0.18);
  border-radius: 999px;
  background: rgba(255, 255, 255, 0.58);
  color: #0f172a;
  font-weight: 600;
  padding: 0.8rem 1.2rem;
  transition: all 0.25s ease;
}

/deep/ .portfolio-section .nav-tabs > li.active > a {
  background: linear-gradient(135deg, #0ea5e9, #2563eb);
  color: white;
  box-shadow: 0 18px 38px rgba(37, 99, 235, 0.22);
}

/deep/ .portfolio-section .nav-tabs > li > a:hover {
  transform: translateY(-2px);
}

/deep/ .portfolio-section .nav-tabs > li > a:after {
  display: none;
}

/deep/ .portfolio-section .tab-content {
  margin-top: 18px;
}

/deep/ .portfolio-section .vueperslides,
/deep/ .portfolio-section .vueperslide,
/deep/ .portfolio-section .vueperslides__parallax-wrapper {
  border-radius: 24px !important;
  overflow: hidden;
}

/deep/ .portfolio-section .vueperslides {
  box-shadow: 0 20px 50px rgba(15, 23, 42, 0.12);
}

/deep/ .portfolio-section .vueperslides__arrow {
  outline: none !important;
  border: none;
  color: rgba(15, 23, 42, 0.6);
}

.btn {
  border-color: rgba(14, 165, 233, 0.24);
  color: #0369a1;
  border-radius: 999px;
  padding: 0.65rem 1.1rem;
}

.btn:hover,
.btn:focus {
  background-color: #0ea5e9;
  border-color: #0ea5e9;
  color: white;
}

.badge {
  background-color: rgba(14, 165, 233, 0.12);
  color: #0369a1;
  transition: all 0.5s;
  font-weight: 600;
  font-size: 0.78rem;
  padding: 0.55rem 0.85rem;
}

.bg-dark4 {
  background-color: rgba(255, 255, 255, 0.08) !important;
}

.date {
  font-size: 0.82rem;
  font-weight: 700;
  opacity: 0.75;
  letter-spacing: 0.04em;
  text-transform: uppercase;
}
</style>
