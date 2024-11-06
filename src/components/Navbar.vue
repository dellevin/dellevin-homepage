<template>
  <nav class="not_index_bg" id="nav">
    <div id="page_site-info">
      <div id="site-title">
        <span class="blogtitle"></span>
      </div>
    </div>
  </nav>
</template>
  
<script>
import Typed from "typed.js";

export default {
  name: "MyNavbar",
  mounted() {
    new Typed(".blogtitle", {
      strings: ["求知若饥，虚心若愚", "Stay Hungry Stay Foolish"],
      startDelay: 300,
      typeSpeed: 100,
      loop: true,
      backSpeed: 50,
      showCursor: true,
    });
  },
};
</script>

<style scoped>
#nav.not_index_bg {
  height: 15rem;
}
#nav {
  position: relative;
  margin-top: -2rem;
  width: 100%;
  background-color: #49b1f5;
  background-attachment: local;
  background-position: center;
  background-size: cover;
}
#page_site-info {
  position: absolute;
  top: 7rem;
  width: 100%;
}
#site-title {
  color: #eee;
  text-align: center;
  text-shadow: 0.1rem 0.1rem 0.2rem rgba(0, 0, 0, 0.15);
  line-height: 1.5;
  font-weight: 700;
  font-size: 2rem;
  animation: titlescale 1s;
}
</style>
  