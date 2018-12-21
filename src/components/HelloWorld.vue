<template>
  <div class="hello">
  <!--  <hello/> -->
<!--    <echarts1/> -->
  <!--  <one/> -->
   <two/>
   <two1/>
     <two2/>
  </div>
</template>

<script>
/* import hello from '@/components/hello' */
/* import echarts1 from '@/components/echarts1' */
/* import one from '@/components/one' */
import two from '@/components/two'
import two1 from '@/components/two1'
import two2 from '@/components/two2'
export default {
  name: 'HelloWorld',
  components:{
/*     hello, */
/*     echarts1, */
  /*   one, */
    two,
    two1,
    two2
  },
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
