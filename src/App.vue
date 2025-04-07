<template>
  <div id="app">
    <router-view />
    <MaxKBChat />
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator'
import MaxKBChat from '@/components/MaxKBChat.vue'

@Component({
  name: 'App',
  components: {
    MaxKBChat
  }
})
export default class extends Vue {}
</script>
