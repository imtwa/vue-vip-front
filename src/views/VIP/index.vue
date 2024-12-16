<template>
  <Header @play-video="updateIframeSrc"></Header>
  <div class="play-layout">
    <div class="page-content_left page-content">
      <div class="container-main_left">
        <iframe
          id="palybox"
          :src="iframeSrcRef"
          allowtransparency="true"
          frameborder="0"
          scrolling="no"
          allowfullscreen="true"
        ></iframe>
      </div>
      <div class="bottom-module_header">
        <div id="tittext">欢迎使用vip视频解析！</div>
        <marquee
          behavior="scroll"
          onmouseover="this.stop()"
          onmouseout="this.start()"
          scrollamount="4"
          >视频解析需耐心等待数秒；如视频未自动播放，请手动点击播放；如视频播放异常，请刷新或切换线路、更换不同平台视频网址播放！</marquee
        >
      </div>
    </div>
    <Right></Right>
  </div>
  <footer class="footer">
    {{ getFooterString() }}
  </footer>
</template>

<script setup lang="ts">
import { ref } from "vue";
import Header from "./components/Header.vue";
import Right from "./components/Right.vue";

const iframeSrcRef = ref(
  "https://jx.xmflv.com/?url=https://www.iqiyi.com/v_186njga2r64.html"
);

function updateIframeSrc(videoInfo: { line: string; url: string }) {
  // 更新 iframe 的 src 属性，将选择的线路和视频 URL 结合
  iframeSrcRef.value = `${videoInfo.line}${encodeURIComponent(videoInfo.url)}`;
}

const getFooterString = (): string => {
  return `Copyright © ${new Date().getFullYear()} imtwa All Rights Reserved 本站所有接口均来自互联网，仅供学习交流使用。`;
};
</script>

<style scoped></style>
