<template>
  <div id="app">
    <!-- <Miss @click.native="refclick"/> -->
    <X/>
  </div>
</template>

<script>
import Miss from './components/Miss'
import X from './components/X'
export default {
  components:{
    Miss,X
  },
  methods: {
      refclick(e){
        console.log(e)
      }
  },
}
</script>
<style>

</style>
