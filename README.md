# vue-checkbox
アニメーション付きのチェックボックス  
[DEMO](https://large014.github.io/vue-checkbox/)

### Usage
```
import CheckBox from './components/CheckBox.vue'

<CheckBox v-model="checkData1" class="boxsample"/>

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
      }
    }
  },
  mounted() {
  },
}
</script>
```
dataでチェックボックスでカスタムしたいプロパティを設定して、v-modelに設定してください。  
[checked] : チェックされたかどうか  
[width] : チェックボックスのdomの長さ  
[title] : タイトル  
[description] : 補足説明  
[shadow_c] : 領域全体のシャドウ色  
[circle_c] : チェックボックスのサークル色  
[checkbox_c] : チェックボックスの色  
[ripple_c] : クリックした際のエフェクト色  
[box_c] : セレクト状態の領域の背景色  

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Run your tests
```
npm run test
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).
