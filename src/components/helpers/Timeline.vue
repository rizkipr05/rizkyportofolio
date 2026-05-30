<template>
  <div>
    <div class="mx-3 mt-3 mb-5 timeline-group">
      <div class="row">
        <div class="col-xl-12 col-bg-12 col-md-12 col-sm-12">
          <p
            class="title1 timeline-heading"
            data-aos="fade"
            data-aos-once="true"
            data-aos-easing="ease-in-out"
            data-aos-mirror="true"
            data-aos-duration="1000"
          >
            {{ data.title }}
          </p>
          <ul
            class="timeline m-0 pt-1"
            v-for="(e, idx) in data.data"
            :key="e.name"
            :style="{ 'transition-delay': idx / 4.2 + 's' }"
            data-aos="fade-up"
            data-offset="10"
            data-aos-once="true"
            data-aos-easing="ease-in-out"
            data-aos-mirror="true"
            data-aos-duration="500"
          >
            <li class="m-0 pb-2">
              <div>
                <div class="px-2 title2">{{ e.name }}, {{ e.place }}</div>
                <div class="px-2 title3">
                  {{ e.degree || e.position }}
                  {{ e.gpa ? "(" + e.gpa + ")" : "" }}
                </div>
                <div class="px-2 date">{{ e.date }}</div>
                <div class="px-2 pb-2 pt-2" style="text-align: justify;">
                  {{ e.description }}
                </div>
                <span
                  class="mx-2 badge p-2 mb-2"
                  v-for="s in e.skills"
                  :key="s"
                  :class="{ 'bg-dark2': nightMode }"
                  >{{ s }}</span
                >
                <p class="m-2"></p>
              </div>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Timeline",
  props: {
    data: {
      type: Object,
    },
    nightMode: {
      type: Boolean,
    },
  },
};
</script>

<style scoped>
.title1 {
  font-size: 1.45rem;
  font-weight: 700;
}

.title2 {
  font-size: 1.1rem;
  font-weight: 600;
}

.title3 {
  font-size: 0.95rem;
  font-weight: 500;
  color: #5f6f87;
}

.badge {
  background-color: rgba(14, 165, 233, 0.12);
  color: #0369a1;
  transition: all 0.5s;
  font-weight: 600;
  padding: 0.55rem 0.85rem;
  border-radius: 999px;
}

.date {
  font-size: 0.82rem;
  font-weight: 600;
  letter-spacing: 0.04em;
  text-transform: uppercase;
  color: #0ea5e9;
}

.timeline-group {
  padding: 18px 4px;
}

.timeline-heading {
  text-transform: capitalize;
  margin-bottom: 28px;
  padding-left: 6px;
}

ul.timeline {
  list-style-type: none;
  position: relative;
}
ul.timeline:before {
  content: " ";
  background: linear-gradient(180deg, rgba(14, 165, 233, 0.34), rgba(59, 130, 246, 0.08));
  display: inline-block;
  position: absolute;
  left: 23px;
  width: 1px;
  height: calc(100% - 42px);
  margin-top: 22px;
  z-index: 400;
}
ul.timeline > li {
  margin: 0 0 22px;
  padding: 0 0 0 28px;
}
ul.timeline > li:before {
  content: " ";
  background: linear-gradient(135deg, #38bdf8, #2563eb);
  display: inline-block;
  position: absolute;
  border-radius: 50%;
  border: 4px solid rgba(255, 255, 255, 0.92);
  box-shadow: 0 0 0 6px rgba(14, 165, 233, 0.12);
  left: 9px;
  width: 28px;
  height: 28px;
  z-index: 400;
}

.bg-dark2 {
  background-color: rgba(255, 255, 255, 0.08) !important;
}

.timeline li > div {
  padding: 20px;
  border-radius: 28px;
  background: linear-gradient(180deg, rgba(255, 255, 255, 0.72), rgba(244, 248, 255, 0.62));
  border: 1px solid rgba(148, 163, 184, 0.18);
  box-shadow: 0 20px 50px rgba(15, 23, 42, 0.06);
  transition: transform 0.28s ease, box-shadow 0.28s ease;
}

.timeline li > div:hover {
  transform: translateY(-4px);
  box-shadow: 0 28px 56px rgba(15, 23, 42, 0.1);
}

.bg-dark2 .title3 {
  color: rgba(231, 238, 252, 0.68);
}

.bg-dark2 .badge {
  color: #7dd3fc;
}

.bg-dark2 .timeline li > div {
  background: linear-gradient(180deg, rgba(15, 26, 44, 0.88), rgba(10, 18, 31, 0.74));
  border-color: rgba(148, 163, 184, 0.1);
}
</style>
