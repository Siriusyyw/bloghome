<template>
  <div class="links">
    <div class="line">
      <Icon size="20">
        <MapSigns />
      </Icon>
      <span class="title">博客导航</span>
    </div>
    <el-row class="link-all" :gutter="20">
      <el-col
        :span="8"
        v-for="(item, index) in linksData"
        :key="item"
        @click="jumpLink(item.link)"
      >
        <div
          class="item cards"
          :style="index < 3 ? 'margin-bottom: 20px' : null"
        >
          <Icon size="26">
            <component :is="item.icon" />
          </Icon>
          <span class="name">{{ item.name }}</span>
        </div>
      </el-col>
    </el-row>
  </div>
</template>

<script setup>
import { ref } from "vue";
import { Icon } from "@vicons/utils";
import {
  MapSigns,
  Home,
  Cloud,
  PhotoVideo,
  BookOpen,
  EdgeLegacy,
  Hotjar,
} from "@vicons/fa";

// 网站链接数据
// 建议不要超出6个，若需要超出请自行调整样式
let linksData = [
  {
    icon: Home,
    name: "主页",
    link: "https://yywen.top/",
  },
  {
    icon: Cloud,
    name: "云盘",
    link: "https://cloud.yywen.top/",
  },
  {
    icon: PhotoVideo,
    name: "相册",
    link: "https://yywen.top/gallery/",
  },
  {
    icon: BookOpen,
    name: "明君书苑",
    link: "https://yywen.top/books/",
  },
  {
    icon: EdgeLegacy,
    name: "网址导航",
    link: "https://yywen.top/tool/",
  },
  {
    icon: Hotjar,
    name: "今日热榜",
    link: "https://tophub.today/",
  },
];

// 链接跳转
const jumpLink = (url) => {
  window.open(url, "_blank");
};
</script>

<style lang="scss" scoped>
.links {
  .line {
    margin: 2rem 0.25rem 1rem;
    font-size: 1.1rem;
    display: flex;
    align-items: center;
    animation: fade;
    -webkit-animation: fade 0.5s;
    .title {
      margin-left: 8px;
      font-size: 1.15rem;
      text-shadow: 0 0 5px #00000050;
    }
  }
  .link-all {
    .item {
      height: 100px;
      width: 100%;
      display: flex;
      align-items: center;
      flex-direction: row;
      justify-content: center;
      animation: fade;
      -webkit-animation: fade 0.5s;

      &:hover {
        transform: scale(1.02);
        background: rgb(0 0 0 / 40%);
        transition: 0.3s;
      }
      .name {
        font-size: 1.1rem;
        margin-left: 8px;
      }
      @media (min-width: 720px) and (max-width: 820px) {
        .name {
          display: none;
        }
      }
      @media (max-width: 720px) {
        height: 80px;
      }
      @media (max-width: 460px) {
        flex-direction: column;
        .name {
          font-size: 1rem;
          margin-left: 0;
          margin-top: 8px;
        }
      }
    }
  }
}
</style>