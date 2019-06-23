<template>
  <div class="ripple">
     <span ref="rippleEffect" class="ripple_effect" :class="{show:isShow}" :style="styles"></span>
  </div>
</template>

<script>
export default {
  name: 'Ripple',
  props: {
    msg: String,
    circleC: String
  },
  data(){
    return{
      isShow: false,
      targetW : 0,
      targetH : 0,
      rippleW : 0,
      rippleH : 0,
      styles:{
        "top" : "0px",
        "left": "100px",
        "width": "100px",
        "height":"100px",
        "backgroundColor":"#000"
      }
    }
  },
  mounted(){
    this.targetH = this.$el.clientHeight;
    this.targetW = this.$el.clientWidth;
    this.styles.backgroundColor = this.circleC;
    if( this.targetW > this.targetH){
      this.styles.width = this.targetW + "px";
      this.styles.height = this.targetW + "px";
      this.rippleW = this.targetW;
      this.rippleH = this.targetW;
    } else {
      this.styles.width = this.targetH + "px";
      this.styles.height = this.targetH + "px";
      this.rippleW = this.targetH;
      this.rippleH = this.targetH;
    }
    this.$rippleEffect.addEventListener("animationend", ()=>{ this.isShow=false ;})
  },
  destroyed(){
      this.$rippleEffect.removeEventListener("animationend", ()=>{ this.isShow=false ;})
  },
  computed:{
    $rippleEffect(){
      return this.$refs.rippleEffect;
    }
  },
  methods:{
    startRipple(event){
      this.styles.top = (event.offsetY - ( this.rippleH / 2)) + "px";
      this.styles.left = (event.offsetX - ( this.rippleW / 2)) + "px";
      this.isShow = true;
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
@keyframes ripple {
    from {
        opacity: 1;
    }
    to {
        transform: scale(2);
        opacity: 0;
    }
}
.ripple {
    height: 100%;
    width: 100%;
    text-align: center;
    line-height: 100px;
    cursor: pointer;
    pointer-events: none;

    overflow: hidden;
    position: absolute;
    top: 0;
    left: 0;
}

/* エフェクト要素 */
.ripple_effect {
    width: 130px;
    height: 130px;
    background-color: aqua;

    position: absolute;
    border-radius: 100%;
    pointer-events: none;
    transform: scale(0);
    opacity: 0;
    &.show{
      animation: ripple 0.6s ease-out;
    }
}

</style>
