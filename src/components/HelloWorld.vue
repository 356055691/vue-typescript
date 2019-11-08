<template>
  <div class="hello">
    <router-link :to='{ path: "/mine", query: { aa: 11, bb: 22} }'><button>mine</button></router-link>
    <h1>{{ msg }}--{{ names }}</h1>
    <input type="text" v-model="txt">
    <p>{{ getTxt }}</p>
    <button @click="add">add</button>
    <p>{{ sum }}</p>
    <Test :name="name"></Test>
    <button @click="go('/mine')">mine</button>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue, Watch } from 'vue-property-decorator';
import Test from './test.vue'

@Component({
  components: {
    Test
  }
})
export default class HelloWorld extends Vue {
  //props
  @Prop() private msg!: string
  @Prop() private names!: string
  //data
  private txt: string = '1'
  private sum: number = 0
  private name: string = 'lmx'
  //computed
  get getTxt(){
    return this.txt
  }
  //methods
  private add(){
    this.sum++
    console.log(`sum : ${this.sum}`)
  }
  private go(path){
    this.$router.push({
      path: path,
      query: {
        aa: '333',
        bb: '444'
      }
    })
  }
  //生命周期
  created(){
    console.log('created')
  }
  //watch
  @Watch('txt') 
  changeTxt(newTxt: string, oldTxt: string){
    console.log(`change txt: ${oldTxt} to ${newTxt}`)
  }
  
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
input {
  width: 240px;
  height: 32px;
  line-height: 32px;
}
</style>