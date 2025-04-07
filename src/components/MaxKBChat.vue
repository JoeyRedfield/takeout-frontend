<template>
  <div class="maxkb-container" ref="maxkbContainer"></div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator'

@Component({
  name: 'MaxKBChat'
})
export default class extends Vue {
  mounted() {
    this.loadMaxKBScript()
  }

  loadMaxKBScript() {
    const script = document.createElement('script')
    script.async = true
    script.defer = true
    script.src = 'http://localhost:8080/api/application/embed?protocol=http&host=localhost:8080&token=ae070ca94189158d'
    script.onload = () => {
      console.log('MaxKB脚本加载成功')
    }
    script.onerror = (error) => {
      console.error('MaxKB脚本加载失败', error)
    }
    document.body.appendChild(script)
  }

  beforeDestroy() {
    // 清理脚本，防止多次加载
    const scripts = document.querySelectorAll('script[src*="localhost:8080/api/application/embed"]')
    scripts.forEach(script => {
      document.body.removeChild(script)
    })
  }
}
</script>

<style scoped>
.maxkb-container {
  /* 可以根据需要添加样式 */
}
</style>
