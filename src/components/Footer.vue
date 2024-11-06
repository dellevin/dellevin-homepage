<template>
  <footer id="footer">
    <div id="footer-wrap">
      <div class="copyright">&copy;2020 - {{ year }} BY Del Levin</div>
    </div>
  </footer>
</template>

<script>
export default {
  name: "MyFooter",
  data() {
    return {
      year: new Date().getFullYear() // 直接在这里获取当前年份
    };
  },
  methods: {

  }
};
</script>

<style scoped>
#footer {
  position: relative;
  margin-top: 1rem;
  background-attachment: local;
  background-position: bottom;
  background-size: cover;
}
#footer-wrap {
  position: relative;
  padding: 2rem 1rem;
  text-align: center;
}
</style>