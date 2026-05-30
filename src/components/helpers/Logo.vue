<template>
  <div class="logo-div">
    <span
      class="logo-title-name"
      :class="{ pgray: !nightMode, 'text-light': nightMode }"
      >{{ name }}</span
    >
    <span class="logo-title-dot pblue">{{ dot }}</span>
  </div>
</template>

<script>
import info from "../../../info";

export default {
  name: "Logo",
  props: {
    nightMode: {
      type: Boolean,
    },
  },
  data() {
    return {
      name: info.logo_name,
      dot: ".",
    };
  },
};
</script>

<style scoped>
.logo-div:hover .logo-title-name {
  letter-spacing: 0px;
  transition: 0.5s all;
}

.logo-title-name {
  font-family: "Space Grotesk", sans-serif;
  font-size: 1.9rem;
  font-weight: 700;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  transition: 0.5s all;
}

.logo-title-dot {
  font-size: 1.8rem;
  font-weight: 700;
}
</style>
