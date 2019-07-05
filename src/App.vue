<template>
  <div id="app">
    <div class="checkBoxList">
      <CheckBox ref="test" v-model="checkData1" class="boxsample"/>
      <CheckBox v-model="checkData2" class="boxsample"/>
      <CheckBox v-model="checkData3" class="boxsample"/>
      <CheckBox v-model="checkData4" class="boxsample"/>
      <div class="debug">
        <p>checkbox1 : {{checkData1}}</p>
        <p>checkbox2 : {{checkData2}}</p>
        <p>checkbox3 : {{checkData3}}</p>
        <p>checkbox4 : {{checkData4}}</p>
      </div>
    </div>
  </div>
</template>

<script>
import CheckBox from './components/CheckBox.vue'
import Ripple from './components/Ripple.vue'
export default {
  name: 'app',
  components: {
    CheckBox,
    Ripple
  },
  data(){
    return{
      checkData1:{
        checked:false,
        width:"340px",
        title:"About start",
        description:"Starting with your OS",
        shadow_c:"rgba(0,0,255,0.3)",
        circle_c:"rgba(0,0,255,0.2)",
        checkbox_c:"rgba(0,0,255,1)",
        ripple_c:"rgba(0,0,255,0.6)",
        box_c:"rgba(0,0,255,0.2)"
      },
      checkData2:{
        checked:false,
        width:"340px",
        title:"Auto update",
        description:"Download and install new version",
        shadow_c:"rgba(50,220,40,0.3)",
        circle_c:"rgba(50,220,40,0.2)",
        checkbox_c:"rgba(50,220,40,1)",
        ripple_c:"rgba(50,220,40,0.6)",
        box_c:"rgba(50,220,40,0.2)"
      },
      checkData3:{
        checked:false,
        width:"340px",
        title:"Don't check auth key",
        description:"All connections will not be checked",
        shadow_c:"rgba(255,198,0,0.3)",
        circle_c:"rgba(255,198,0,0.2)",
        checkbox_c:"rgba(255,198,0,1)",
        ripple_c:"rgba(255,198,0,0.6)",
        box_c:"rgba(255,198,0,0.2)"
      },
      checkData4:{
        checked:true,
        width:"340px",
        title:"Success all",
        description:"Everyone will be fine",
        shadow_c:"rgba(255,0,0,0.3)",
        circle_c:"rgba(255,0,0,0.2)",
        checkbox_c:"rgba(255,0,0,1)",
        ripple_c:"rgba(255,0,0,0.6)",
        box_c:"rgba(255,0,0,0.2)"
      },
    }
  },
  mounted() {
  },
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
}
.boxsample{
  margin-bottom: 5px;
}

.debug{
  padding-left: 20px;
  margin-top: 20px;
  text-align: left;
}
.debug p{
  margin-bottom: 10px;
}

.rippletest{
  width: 200px;
  height: 200px;
  border: 1px solid #CCC;
  position: relative;
}
</style>
