<template>
  <div id="app">
    <div class="checkBoxList">
      <CheckBox ref="test" @check-event="onClick($event)" class="boxsample" width="320px" title="About start" description="Starting with your OS" shadow_c="rgba(0,0,255,0.3)" circle_c="rgba(0,0,255,0.4)" checkbox_c="rgba(0,0,255,1)" box_c="rgba(0,0,255,0.8)"/>
      <CheckBox class="boxsample" width="320px" title="Auto update" description="Download and install new version" shadow_c="rgba(50,220,40,0.3)" circle_c="rgba(50,220,40,0.4)" checkbox_c="rgba(50,220,40,1)" box_c="rgba(50,220,40,0.8)"/>
      <CheckBox class="boxsample" width="320px" title="Don't check auth key" description="All connections will not be checked" shadow_c="rgba(255,198,0,0.3)" circle_c="rgba(255,198,0,0.4)" checkbox_c="rgba(255,198,0,1)" box_c="rgba(255,198,0,0.8)"/>
      <CheckBox class="boxsample" width="320px" title="Success all" description="Everyone will be fine" shadow_c="rgba(255,0,0,0.3)" circle_c="rgba(255,0,0,0.4)" checkbox_c="rgba(255,0,0,1)" box_c="rgba(255,0,0,0.8)"/>
    </div>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import CheckBox from './components/CheckBox.vue'

export default {
  name: 'app',
  components: {
    CheckBox
  },
  data(){
    return{
    }
  },
  mounted() {
    this.$refs.test.data
    console.log('value = ' + this.$refs.test.checked);
  },
  methods: {
    onClick( type ){
      console.log('1value = ' + this.$refs.test.checked);
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.checkBoxList{
  width: 335px;
  margin: 0 auto;
  /* display: flex; */
  /* align-items: flex-start; */
}
.boxsample{
  margin-bottom: 5px;
}
</style>
