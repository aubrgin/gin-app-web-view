<template>
  <div class="gin-app-web-view">
    <template v-if="computedUrl">
      <webview :src="computedUrl" />
    </template>
    <template v-else>
      <gin-input v-model="tempUrl" />
      <gin-button @click="dataUrl = tempUrl">
        Load Page
      </gin-button>
    </template>
  </div>
</template>


<script>
import { GinInput, GinButton } from '@aubrgin/gin-components';

export default {
   name: 'WebView',
   components: {
     GinInput,
     GinButton,
   },
   props: {
     url: {
       type: String,
       default: '',
     },
   },
   computed: {
     computedUrl() {
       return this.url || this.dataUrl;
     },
   },
   data() {
     return {
       dataUrl: '',
       tempUrl: '',
     };
   },
}
</script>

<style lang="scss">
 .gin-app-web-view {
   height: 100%;
   width: 100%;
   overflow-x: hidden;

   webview {
     height: 100%;
     width: 100%;
   }
 }
</style>
