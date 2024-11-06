<template>
  <div id="app">
    <MyNavbar />
    <main id="content-outer">
      <div class="layout_page" id="content-inner">
        <MyContactInfo />
        <MyContent />
      </div>
    </main>
    <MyFooter />
  </div>
</template>

<script>
import MyNavbar from './components/Navbar.vue';
import MyFooter from './components/Footer.vue';
import MyContactInfo from './components/ContactInfo.vue';
import MyContent from './components/Content.vue';

export default {
  name: 'App',
  components: {
    MyNavbar,
    MyFooter,
    MyContactInfo,
    MyContent
  }
};
</script>

<style>
* {
    box-sizing: border-box;
}
html {
    height: 100%;
    -webkit-user-select: none; /* Safari */
    -moz-user-select: none;    /* Firefox */
    -ms-user-select: none;     /* Internet Explorer/Edge */
    user-select: none;         /* Non-prefixed version, currently supported by Chrome, Opera and Firefox */
}
body {
    position: relative;
    min-height: 100%;
    background: #eee;
    color: #4c4948;
    font-size: 14px;
    font-family: Lato, Helvetica Neue For Number, -apple-system, BlinkMacSystemFont, Segoe UI, Roboto, PingFang SC, Hiragino Sans GB, "Microsoft JhengHei", "MicrMicrosoft YaHei", Helvetica Neue, Helvetica, Arial, sans-serif;
    line-height: 2;
}
body {
    margin: 0;
}
h1, h2, h3, h4, h5, h6 {
    position: relative;
    margin: 1rem 0 .7rem;
    color: #344c67;
    font-weight: 700
}
hr:before {
    position: absolute;
    top: -10px;
    left: 5%;
    z-index: 1;
    color: #49b1f5;
    content: '\f0c4';
    font: normal normal normal 14px/1 FontAwesome;
    font-size: 20px;
    transition: all 1s ease-in-out;
}
hr {
    position: relative;
    margin: 2rem auto;
    width: calc(100% - 4px);
    border: 2px dashed #a4d8fa;
    background: #fff;
}
hr {
    box-sizing: content-box;
    height: 0;
    overflow: visible;
}
strong{
    color: #FF0066;
}

.layout_page {
    display: flex;
    -webkit-box-align: start;
    align-items: flex-start;
    margin: 0 auto;
    padding: 0 5px;
    max-width: 1400px;
}

::-webkit-scrollbar {
    width: 5px;
    height: 5px
}

/* 滚动条滑块的样式 */
::-webkit-scrollbar-thumb {
    background-color: #66afef; /* 滑块颜色 */
    border-radius: 4px; /* 滑块的圆角 */
    transition: background-color 0.3s ease; /* 鼠标悬停时的平滑过渡 */
}
/* 鼠标悬停在滑块上的样式 */
::-webkit-scrollbar-thumb:hover {
    background-color: #2a77b8; 
}

::-webkit-scrollbar-track {
    background-color: transparent
}
</style>
