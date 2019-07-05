<template>
  <div ref="checkboxArea" class="checkboxArea" :class="{checked:checked}" :style="styles" @mousedown="onClick">
    <Ripple ref="ripple" :circleC="ripple_c" clickable="none"/>
    <label>
      <input type='checkbox' class="checkbox" v-model="checked"/>
      <div class="boxparts">
        <span class="box"></span>
      </div>
      <div class="textArea">
        <p class="title">{{title}}</p>
        <p class="description">{{description}}</p>
      </div>
    </label>
  </div>
</template>

<script>
import Ripple from './Ripple.vue'

export default {
  name: 'CheckBox',
  components: {
    Ripple
  },
  data(){
    return{
      checked: false,
      title:String,
      description:String,
      shadow_c:String,
      circle_c:String,
      box_c:String,
      checkbox_c:String,
      ripple_c:String,
    }
  },
  beforeMount(){
    this.boxwidth = this.value.width;
    this.shadow_c = this.value.shadow_c;
    this.circle_c = this.value.circle_c;
    this.checkbox_c = this.value.checkbox_c;
    this.box_c = this.value.box_c;
    this.ripple_c = this.value.ripple_c;
    this.rippleC = this.value.circle_c;
  },
  mounted(){
    this.checked = this.value.checked;
    this.title = this.value.title;
    this.description = this.value.description;
  },
  updated(){
    this.$emit('input', {checked:this.checked})
  },
  props: ['value'],
  computed:{
    $checkboxArea() {
      return this.$refs.checkboxArea
    },
    styles(){
      return{
        '--width':this.boxwidth,
        '--shadow_c':this.shadow_c,
        '--circle_c':this.circle_c,
        '--checkbox_c':this.checkbox_c,
        '--box_c':this.box_c,
      }
    }
  },
  methods:{
    onClick(e){
      if(!this.checked){
        this.$refs.ripple.startRipple(e)
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

@keyframes check_anim{
  from{
    height: 0;
  }
}

.checkboxArea{
  //---- デフォルト値の設定
  --width: 300px;
  --shadow_c: rgba(0,0,255,0.3);
  --circle_c: rgba(0,0,255,0.3);
  --checkbox_c: rgba(0,0,255,0.5);
  --box_c: rgba(0,0,255,0.3);
  position: relative;
  width: var(--width);
  border-radius: 4px;
  transition: background-color .01s linear;
  &.checked{
    background-color: var(--circle_c);
  }
}
.checkboxArea:hover{
  box-shadow: 0 2px 8px var(--shadow_c);
  .boxparts:before{
    opacity: 1;
    transform: translate(-50%, -50%) scale(1);
    transform-origin: 50% 50%;
  }
}

.checkbox{
  display: none;
}

.boxparts{
  position: absolute;
  top: 50%;
  left: 2px;
  transform: translate(0%, -50%);
  display: inline-block;
  width:53px;
  height: 53px;

  .box{
    position: absolute;
    top: 49.7%;
    left: 49.0%;
    transform: translate( calc(-50% + 0px), -50%);
    width: 19px;
    height: 19px;
    border: 2px solid var(--checkbox_c);
    border-radius: 3px;
    z-index: 1;
    backface-visibility: hidden;
  }
  .box:before{
    content: '';
    position: absolute;
    bottom: 25%; left: 41%;

    font-size: 0em;
    width: .15em;
    height: .5em;
    background-color: #fff;

    transform-origin: center bottom;
    transform:  translateX(-50%) scaleX(-1) rotate(-135deg) translateY(.5em); 
  }
  .box:after{
    content: '';
    position: absolute;
    bottom: 30%; left: 41%;

    font-size: 0em;
    width: .15em;
    height: .94em;
    background-color: #FFF;

    transform-origin: center bottom;
    transform: translateX(-50%) rotate(45deg) translate(.05em,.125em);
  }
}
.boxparts::before{
  content: "";
  display: block;
  position: absolute;
  top: 50%;
  left: 50%;
  width: 44px;
  height: 44px;
  border-radius: 50%;
  background-color: var(--circle_c);
  transition: opacity .05s linear, transform .1s linear;
  opacity: 0;
  transform-origin: 50% 50%;
  transform: translate(-50%, -50%) scale(0.6);
}

//--- チェックON
.checkbox:checked + .boxparts .box:before{
  font-size: 0.5em;
  animation:check_anim .05s linear both;
}
.checkbox:checked + .boxparts .box:after{
  font-size: 0.5em;
  animation: check_anim .05s .05s linear both;
}
.checkbox:checked + .boxparts .box{
  background-color: var(--checkbox_c);
}
.checkbox:checked + .boxparts::before{
  opacity: 0;
}

.textArea{
  text-align: left;
  padding: 13px 20px 13px 55px;
  pointer-events: none;
}

.title{
  font-weight: 600;
  margin-bottom: 5px;
  user-select: none;
}
.description{
  color: #888;
  user-select: none;
}
</style>
