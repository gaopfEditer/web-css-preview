<script setup lang="ts">
setTimeout(()=>{

// 容器元素
const container = document.querySelector(".container");

// 计算总内容宽度
function checkOverflow() {
  let totalWidth = 0;

  // 遍历所有span累加宽度
  const spans = container.querySelectorAll("span");
  spans.forEach((span) => {
    const style = getComputedStyle(span);
    totalWidth +=
      span.offsetWidth +
      parseFloat(style.marginLeft) +
      parseFloat(style.marginRight);
  });

  // 获取容器可用宽度（去除padding）
  const containerStyle = getComputedStyle(container);
  const containerWidth =
    container.offsetWidth -
    parseFloat(containerStyle.paddingLeft) -
    parseFloat(containerStyle.paddingRight);

  // 切换溢出状态
  container.classList.toggle("overflow", totalWidth > containerWidth);
}

// 初始化检测
checkOverflow();

// 窗口变化时重新检测
window.addEventListener("resize", checkOverflow);
}, 0)
</script>
<template>
  <div class="page">
    <div class="container">
      <span>正常长度文本</span>
      <span>中等长度内容</span>
      <span>这是非常非常非常非常非常长的span内容</span>
      <span>短文本</span>
      <span>另一个示例</span>
    </div>
  </div>
</template>

<style scoped>
.page {
  width: 300px;
  height: 200px;
  background-color: #f1f1f1;
  overflow: hidden;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 24px;
  font-weight: bold;
  opacity: 0;
  transform: scaleX(0);
  transform-origin: center;
  animation: openAnimation 1s ease-in-out forwards;
}

@keyframes openAnimation {
  0% {
    transform: scaleX(0);
    opacity: 0;
  }
  50% {
    transform: scaleX(1.2);
    opacity: 1;
  }
  100% {
    transform: scaleX(1);
    opacity: 1;
  }
}

.container {
  width: 300px; /* 容器固定宽度 */
  border: 1px solid #ccc;
  padding: 8px;
  overflow: hidden; /* 隐藏溢出内容 */
  white-space: nowrap; /* 禁止换行 */
  position: relative; /* 为伪元素定位准备 */
}

/* 通过伪元素添加省略号 */
.container::after {
  content: "";
  display: none; /* 默认隐藏 */
  position: absolute;
  right: 0;
  top: 0;
  bottom: 0;
  width: 30px; /* 省略号区域宽度 */
  background: linear-gradient(
    90deg,
    rgba(255, 255, 255, 0) 0%,
    rgba(255, 255, 255, 1) 30%
  );
}

/* 显示省略号的类 */
.container.overflow::after {
  display: block;
}
.container.overflow::before {
  content: "...";
  position: absolute;
  right: 5px;
  top: 50%;
  transform: translateY(-50%);
  z-index: 2;
}
</style>

<route lang="yaml">
name: 开屏动画
meta:
  layout: demo
</route>
