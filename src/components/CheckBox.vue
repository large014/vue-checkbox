<template>
  <div class="checkboxArea">
    <label>
      <input type='checkbox' class="checkbox"/>
      <div class="boxparts">
        <!-- <span class="circle"></span> -->
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
export default {
  name: 'HelloWorld',
  props: {
    title: String,
    description:String
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
  position: relative;
  display: inline-block;
  border-radius: 4px;
  padding: 20px;
}
.checkboxArea:hover{
  box-shadow: 0 0 6px rgba(0,0,255,0.3);
  .boxparts:before{
    opacity: 1;
      transform: translate(-50%, -50%) scale(1);
  }
}

.checkbox{
  display: none;
}

.boxparts{
  position: absolute;
  top: 50%;
  left: 20px;
  transform: translate(0%, -50%);
  display: inline-block;
  width:53px;
  height: 53px;
  border: 1px solid #CCC;

  .box{
    position: absolute;
    top: 49.7%;
    left: 50%;
    transform: translate( calc(-50% + 0px), -50%);
    width: 18px;
    height: 18px;
    border: 2px solid #999;
    border-radius: 3px;
    z-index: 1;
  }
  .box:before{
    content: '';
    position: absolute;
    bottom: 25%; left: 40%;

    font-size: 0em;
    width: .15em;
    height: .5em;
    background-color: currentColor;

    transform-origin: center bottom;
    transform:  translateX(-50%) scaleX(-1) rotate(-135deg) translateY(.5em); 
  }
  .box:after{
    content: '';
    position: absolute;
    bottom: 30%; left: 40%;

    font-size: 0em;
    width: .15em;
    height: .94em;
    background-color: currentColor;

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
  // transform: translate(-50%, -50%);
  width: 48px;
  height: 48px;
  border-radius: 50%;
  background-color: aquamarine;
  transition: opacity .1s linear, transform .1s linear;
  opacity: 0;
  transform-origin: 50% 50%;
  transform: translate(-50%, -50%) scale(0.6);
}

.checkbox:checked + .boxparts .box:before{
  font-size: 0.5em;
  animation:check_anim .1s linear both;
}


.checkbox:checked + .boxparts .box:after{
  font-size: 0.5em;
  animation: check_anim .1s .1s linear both;
}

.textArea{
  display: inline-block;
  text-align: left;
  padding-left: 55px;
}

.title{
  font-weight: 600;
  margin-bottom: 5px;
}
.description{
  color: #888;
}
</style>
