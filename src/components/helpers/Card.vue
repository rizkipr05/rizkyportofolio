<template>
  <div class="my-3 mx-3">
    <div
      class="card smcard"
      :class="{
        'pcard-dark': nightMode,
        pcard: !nightMode,
        'bg-dark3': nightMode,
      }"
    >
      <div class="image-frame" style="height: 200px;">
        <img
          class="card-img-top"
          :src="portfolio.pictures[0].img"
          alt="Card image cap"
        />
      </div>
      <div class="card-body pborder-top">
        <div class="meta-row mb-3">
          <span class="project-type">{{ portfolio.category }}</span>
          <span class="project-date">{{ portfolio.date }}</span>
        </div>
        <h5 class="title2">{{ portfolio.name }}</h5>
        <div>
          <div class="pb-1 bheight">
            <span
              class="badge mr-2 mb-2 "
              v-for="tech in portfolio.technologies"
              :key="tech"
              :class="{ 'bg-dark4': nightMode }"
              >{{ tech }}</span
            >
          </div>
          <p
            class="title3 m-0 pb-2 pheight pt-1"
            v-html="
              portfolio.description.length > 100
                ? portfolio.description.substring(0, 105) + '...'
                : portfolio.description
            "
          >
          </p>
        </div>
        <div class="text-center mt-2">
          <button
            href=""
            class="btn-sm btn btn-outline-secondary no-outline"
            @click.prevent="showModal"
          >
            read more
          </button>
          <button
            href="#"
            class="btn-sm btn btn-outline-secondary no-outline ml-4"
            v-if="portfolio.visit"
            @click.prevent="open(portfolio.visit)"
          >
            visit website
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Card",
  props: {
    portfolio: {
      type: Object,
    },
    nightMode: {
      type: Boolean,
    },
  },
  methods: {
    open(url) {
      window.open(url, "_blank");
    },
    showModal() {
      this.$emit("show", this.portfolio);
    },
  },
};
</script>

<style scoped>
img {
  border-top-left-radius: 22px;
  border-top-right-radius: 22px;
  max-width: 100%;
  max-height: 100%;
  object-fit: cover;
}

.img-div img {
  /* object-fit: cover;
    overflow: hidden; */
  margin-left: auto;
  margin-right: auto;
  display: block;
  /* object-position: 50% 120%;
    max-width: 300px !important; */
}

.bheight {
  height: 65px;
  overflow: auto;
}

.pheight {
  height: 110px;
  max-height: 130px;
  overflow: auto;
  text-align: justify;
}

div.img-div {
  position: absolute;
  width: 100%;
  height: 100%;
}
.pborder-top {
  border-top: 1px solid rgba(148, 163, 184, 0.18);
}

.pcard {
  background-color: rgba(255, 255, 255, 0.72);
  border-radius: 22px;
  border: none;
  box-shadow: 0 24px 55px rgba(15, 23, 42, 0.08);
  transition: all 0.5s;
  height: 500px;
  overflow: hidden;
  border: 1px solid rgba(148, 163, 184, 0.18);
}

.pcard:hover {
  transition: all 0.5s;
  transform: translateY(-8px);
  box-shadow: 0 28px 65px rgba(15, 23, 42, 0.12);
}

.pcard-dark {
  border-radius: 22px;
  border: none;
  background-color: rgba(255, 255, 255, 0.04) !important;
  transition: all 0.5s;
  height: 500px;
  overflow: hidden;
  border: 1px solid rgba(148, 163, 184, 0.12);
}

.pcard-dark:hover {
  transition: all 0.5s;
  transform: translateY(-8px);
  box-shadow: 0 28px 65px rgba(0, 0, 0, 0.22);
}

.pcard-body {
  border-top: 1px solid rgb(220, 220, 220);
  z-index: -1;
  background-color: rgb(253, 254, 255);
}

.title {
  font-size: 30px;
  font-weight: 500;
}
.title1 {
  font-size: 24px;
  font-weight: 400;
}

.title2 {
  font-size: 1.2rem;
  font-weight: 700;
}

.title3 {
  font-size: 0.95rem;
  font-weight: 400;
  color: #5f6f87;
}

.badge {
  background-color: rgba(14, 165, 233, 0.12);
  color: #0369a1;
  transition: all 0.5s;
  font-weight: 600;
  font-size: 0.78rem;
  padding: 0.55rem 0.85rem;
}

.btn {
  border-color: rgba(14, 165, 233, 0.24);
  color: #0369a1;
  border-radius: 999px;
  padding: 0.55rem 1rem;
}

.btn:hover {
  background-color: #0ea5e9;
  border-color: #0ea5e9;
  color: white;
}

.btn:focus {
  background-color: #0ea5e9;
  border-color: #0ea5e9;
  color: white;
}

.bg-dark3 {
  background-color: rgba(255, 255, 255, 0.04);
}

.bg-dark4 {
  background-color: rgba(255, 255, 255, 0.08) !important;
}

.image-frame {
  overflow: hidden;
}

.image-frame img {
  transition: transform 0.5s ease;
}

.pcard:hover .image-frame img,
.pcard-dark:hover .image-frame img {
  transform: scale(1.04);
}

.meta-row {
  display: flex;
  justify-content: space-between;
  gap: 12px;
  align-items: center;
}

.project-type,
.project-date {
  font-size: 0.78rem;
  font-weight: 700;
  letter-spacing: 0.05em;
  text-transform: uppercase;
}

.project-type {
  color: #0ea5e9;
}

.project-date {
  color: #94a3b8;
}
</style>
