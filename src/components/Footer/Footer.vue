<template>
  <footer class="w-full max-w-[1666px] mt-36 pb-4">
    <main class="m-auto pt-4 flex flex-col-reverse md:flex-row justify-between gap-2 md:gap-16 w-full max-w-[1666px] border-t">
      
    </main>
    <!-- 保持居中样式，添加链接 -->
    <section class="[&>p]:text-xs [&>p]:w-full [&>p]:py-[6px] [&>p]:text-center">
        <p>海阔图床是<a href="https://167891.xyz" target="_blank" class="text-slate-600 hover:text-slate-800 underline decoration-1 underline-offset-2">旧识桥</a>支持的文件上传项目，致力于为用户提供稳定的永久存储服务。</p>
        <p class="text-red-600">注意:上传违反中国大陆、香港及美国法律的图片将会直接删除，并封禁设备IP。</p>
    </section>
    <p class="mt-2 text-xs text-center text-slate-500">本站已稳定运行：{{ runTime }}</p>
    <p class="mt-2 text-xs text-center text-slate-500">©2025 <a href="https://167891.xyz" target="_blank" class="text-slate-600 hover:text-slate-800 underline decoration-1 underline-offset-2">旧识桥</a> | 本站稳定运行</p>
  </footer>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

// 定义站点启动时间（你可以修改为实际的上线时间）
const LAUNCH_DATE = new Date('2025-12-31 00:00:00')
const runTime = ref('')
let timer = null

// 计算运行时长的函数
const calculateRunTime = () => {
  const now = new Date()
  const diff = now - LAUNCH_DATE
  
  // 计算天、时、分、秒
  const days = Math.floor(diff / (1000 * 60 * 60 * 24))
  const hours = Math.floor((diff % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60))
  const minutes = Math.floor((diff % (1000 * 60 * 60)) / (1000 * 60))
  const seconds = Math.floor((diff % (1000 * 60)) / 1000)
  
  // 格式化显示
  runTime.value = `${days}天 ${hours}时 ${minutes}分 ${seconds}秒`
}

// 挂载时启动定时器，每秒更新一次
onMounted(() => {
  calculateRunTime() // 初始化
  timer = setInterval(calculateRunTime, 1000)
})

// 卸载组件时清除定时器，避免内存泄漏
onUnmounted(() => {
  if (timer) clearInterval(timer)
})
</script>
