<template>
  <div class="aside_content" id="content-inner">
    <div class="card-widget card-info">
      <div class="card-content">
        <div class="card-info-avatar is-center">
          <img class="avatar-img" :src="avatarSrc" alt="avatar" />
          <div class="author-info__name">Del Levin</div>
          <div class="author-info__description" v-html="description"></div>
        </div>
        <div class="card-info-social-icons is-center">
          <a
            v-for="(link, icon) in socialLinks"
            :key="icon"
            :href="link"
            target="_blank"
            class="social-icon"
          >
            <i :class="['fa', icon]"></i>
          </a>
        </div>
      </div>
    </div>

    <div class="card-widget card-info">
      <div class="card-content">
        <div class="item-headline">
          <i class="fa fa-connectdevelop" aria-hidden="true"></i>
          <span style="font-weight: 1000">联系方式</span>
        </div>
        <div class="selectable">
          <span style="font-weight: 1000">微信 ：</span> E-Levin_
          <br />
          <span style="font-weight: 1000">扣扣 ：</span> 1754084631
          <br />
          <span style="font-weight: 1000">邮箱 ： </span>dellevin99@gmail.com
        </div>
      </div>
    </div>

    <div class="card-widget card-info">
      <div class="card-content">
        <div class="item-headline">
          <i class="fa fa-pagelines" aria-hidden="true"></i>
          <span>诗词</span>
        </div>
        <div>毕竟几人真得鹿，不知终日梦为鱼。</div>
        <!-- <div id="jinrishici-sentence"></div> -->
      </div>
    </div>

    <div class="card-widget card-info">
      <div class="card-content">
        <div class="item-headline">
          <i class="fa fa-calendar" aria-hidden="true"></i>
          <span>经历</span>
        </div>
        <div class="experience-line">
            <div class="experience-item" v-for="(item, index) in experiences" :key="index">
            <div class="experience-description">{{ item.description }}</div>
            <div class="experience-date">{{ item.date }}</div>
            </div>
        </div>
      </div>
    </div>


  </div>
</template>

<script>
export default {
  name: "MyContactInfo",
  data() {
    return {
      avatarSrc: "https://img.ittoolman.com/2024/10/23/e2378b86dee7d.png",
      description:
        "99青年，全栈开发者，数据分析，啥都略懂, <del>学生</del>，缺乏社会的毒打",
      socialLinks: {
        "fa-github": "https://github.com/dellevin",
        "fa-weibo": "https://weibo.com/u/6094785105",
        "fa-steam": "https://steamcommunity.com/profiles/76561199155776053/",
        "fa-telegram": "https://t.me/levin092",
      },
      experiences: [
        { description: "未来还须努力", date: "2024.10~至今" },
        { description: "重启了我的网站", date: "2024.10" },
        { description: "大学生涯就此结束", date: "2022.07" },
        { description: "购买了第一台服务器", date: "2020.02.02" },
      ],
    };
  },
};
</script>

<style scoped>
.is-center {
  text-align: center;
}
.aside_content {
  width: 25%;
  position: relative;
  min-height: 100%;
  /* background: #f9f9f9; */
  color: #4c4948;
  font-size: 14px;
  font-family: Lato, Helvetica Neue, Arial, sans-serif;
  line-height: 1.6;
  padding: 20px;
  border-radius: 8px;
  /* box-shadow: 0px 4px 8px rgba(0, 0, 0, 0.1); */
}

.card-widget {
  margin-top: 10px;
  padding: 20px;
  background: white;
  border-radius: 8px;
  box-shadow: 0px 4px 8px rgba(0, 0, 0, 0.1);
}

.card-info-avatar img {
  width: 100px;
  height: 100px;
  border-radius: 50%;
  border: 4px solid #e0e0e0;
  margin-bottom: 15px;
}

.author-info__name {
  font-weight: bold;
  font-size: 1.2rem;
  color: #333;
}

.author-info__description {
  margin-top: 5px;
  font-size: 0.9rem;
  color: #666;
}

.card-info-social-icons {
  margin-top: 15px;
}

.card-info-social-icons .social-icon {
  margin: 0 10px;
  color: #4c4948;
  font-size: 1.5rem;
  transition: color 0.3s ease;
}

.card-info-social-icons .social-icon:hover {
  color: #333;
}

.item-headline {
  font-size: 0.9rem;
  margin-bottom: 10px;
}
.item-headline span {
  margin-left: 0.7rem;
}
.selectable {
  -webkit-user-select: text; /* Safari */
  -moz-user-select: text; /* Firefox */
  -ms-user-select: text; /* Internet Explorer/Edge */
  user-select: text; /* Non-prefixed version, currently supported by Chrome, Opera and Firefox */
}

/* 时间轴 */
.experience-line {
  position: relative;
  margin-left: 5px;
  padding-left: 20px;
  border-left: 2px solid #ddd;
}

.experience-item {
  margin-bottom: 20px;
  padding-left: 10px;
  position: relative;
}

.experience-item::before {
  content: "";
  position: absolute;
  left: -25px;
  top: 10px;
  width: 8px;
  height: 8px;
  background-color: #333;
  border-radius: 50%;
}

.experience-description {
  font-weight: bold;
  margin-bottom: 5px;
}

.experience-date {
  color: #666;
  font-size: 0.9rem;
}
</style>
