<template>
  <div>
    mine
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue, Watch } from 'vue-property-decorator';

@Component
export default class Mine extends Vue {
  created(){
    console.log('mine');
  }
}
</script>

<style scoped>
</style>
