<template>
  <div>
    子组件{{ name }} {{ newName }}
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue, Watch } from 'vue-property-decorator';
import funA from '../../utils/common';

@Component
export default class HelloWorld extends Vue {
  @Prop() private name!: string
  private newName: string = 'haha'
  created(){
    console.log('子组件created');
  }
  mounted(){
    console.log('子组件mounted');
    this.myFun();
    console.log(funA.sonA(111, 222));
    console.log(funA.sonB('111','222'));
  }
  private myFun() {
    this.newName = 'mq';
    console.log('myFun', this.newName);
  }
}
</script>

<style scoped>
</style>
