<template>
  <div class="step1-container">
    <div class="progress-container">
      <FilterBar
        :steps="['加入须知', '白名单填写', '等待审核', '下载整合包']"
        :currentStep="1"
      />
    </div>
    <div class="welcome-message">
      <h2>欢迎加入ImpartLab服务器</h2>
      <p>在开始之前，您需要：</p>
        <p>1、加入我们的QQ群，以便及时获取服务器动态和与其他玩家交流</p>
        <p>2、仔细阅读服务器手册，了解服务器规则和玩法</p>
    </div>

    <!-- 主要内容区域 -->
    <div class="content-container">
        <el-button type="primary" class="action-button" @click="joinQQGroup">
          <el-icon><ChatDotRound /></el-icon>
          加入QQ群
        </el-button>
        <el-button type="success" class="action-button" @click="readManual">
          <el-icon><Document /></el-icon>
          阅读手册
        </el-button>
    </div>

    <!-- 底部操作栏 -->
    <div class="bottom-bar">
      <el-button type="primary" class="next-button" @click="goToNextStep">
        下一步
        <el-icon class="el-icon--right"><ArrowRight /></el-icon>
      </el-button>
    </div>
  </div>
</template>

<script setup>
import { useRouter } from 'vue-router';
import FilterBar from './common/FilterBar.vue';
import { ChatDotRound, Document, ArrowRight } from '@element-plus/icons-vue';
import {QQ_GROUP, WIKI} from "@/config/links.js";

const router = useRouter();

const joinQQGroup = () => {
  window.open(QQ_GROUP);
};

const readManual = () => {
  window.open(WIKI);
};

const goToNextStep = () => {
  router.push('/whitelist-step2');
};
</script>

<style scoped>
.step1-container {
  display: flex;
  flex-direction: column;
  position: relative;
  padding-bottom: 80px;
  width: 100%;
  box-sizing: border-box;
}

.progress-container {
  width: 100%;
  margin: 0 auto;
  padding: 0 5%;
  box-sizing: border-box;
  display: flex;
  justify-content: center;
  align-items: center;
}

.content-container {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 20px;
}

.welcome-message {
  padding: 40px 30px;
}

.action-button {
  width: 180px;
  height: 50px;
  font-size: 16px;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 8px;
  border-radius: 8px;
  transition: all 0.3s ease;
}

.action-button:hover {
  transform: translateY(-2px);
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
}

.bottom-bar {
  position: fixed;
  bottom: 0;
  left: 0;
  right: 0;
  height: 80px;
  background: rgba(255, 255, 255, 0.95);
  backdrop-filter: blur(10px);
  display: flex;
  justify-content: center;
  align-items: center;
  box-shadow: 0 -2px 10px rgba(0, 0, 0, 0.05);
  z-index: 1000;
}

.next-button {
  width: 200px;
  height: 50px;
  font-size: 16px;
  border-radius: 8px;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 8px;
  transition: all 0.3s ease;
}

.next-button:hover {
  transform: translateY(-2px);
  box-shadow: 0 4px 12px rgba(64, 158, 255, 0.2);
}
</style> 