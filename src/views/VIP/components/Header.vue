<template>
  <div id="ssi-header">
    <div class="site_head_placeholder"></div>
    <div class="top-nav-wrap head_inner">
      <div class="logo_nav">
        <a id="header-logo" class="header-logo-wrap" href="/"></a>
        <div class="header-nav-wrap">
          <div id="main-top-nav-wrap"></div>
        </div>
      </div>

      <div class="mod_search">
        <input
          type="text"
          v-model="videoUrlRef"
          class="form-control url-text"
          placeholder="粘贴视频网址到此处点击解析播放即可！"
          title="粘贴视频网址到此处点击解析播放即可！"
          autocomplete="off"
        />
        <select
          v-model="selectedLineRef"
          class="url-c url-text"
          title="如发现视频无法正常播放请尝试更换视频线路！"
          id="jk"
        >
          <option value="https://jx.xmflv.com/?url=" selected>默认一</option>
          <option value="https://www.ckplayer.vip/jiexi/?url=">推荐二</option>
          <option value="https://z1.m1907.top/?jx=">剧名/链接</option>
          <option value="https://jx.m3u8.tv/jiexi/?url=">线路四</option>
          <option value="https://www.playm3u8.cn/jiexi.php?url=">线路五</option>
          <option value="https://www.pangujiexi.com/jiexi/?url=">
            无法播放时
          </option>
          <option value="https://jx.xmflv.cc/?url=">请切换接口</option>
          <option value="https://www.yemu.xyz/?url=">线路八</option>
          <option value="https://www.8090g.cn/?url=">线路九</option>
          <option value="https://bd.jx.cn/?url=">线路十</option>
        </select>

        <button
          type="button"
          class="btn btn-default btn-play"
          title="点击开始解析并开始播放"
          @click="handlePlay"
        >
          解析播放
        </button>
      </div>
      <div class="support">
        <a href="#" title="支持">
          <img src="../../../assets/img/support.png" alt="支持" />
        </a>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";

const videoUrlRef = ref("");
const selectedLineRef = ref("https://jx.xmflv.com/?url=");

const emit = defineEmits<{
  (e: "play-video", videoInfo: { url: string; line: string }): void;
}>();

function handlePlay() {
  // 触发自定义事件 'play-video' 并传递 videoUrl 和 selectedLine
  const videoInfo = {
    url: videoUrlRef.value,
    line: selectedLineRef.value,
  };
  emit("play-video", videoInfo);
}
</script>

<style lang="scss" scoped></style>
