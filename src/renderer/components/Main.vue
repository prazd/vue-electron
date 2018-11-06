<template>
<div>
<main>



<a href="/" class="bot1">Выход</a>

<div class="block">
Номинальное напряжение питания <br>{{U}} % Uном
  <range-slider
    class="slider"
    min="65"
    max="110"
    step="5"
    v-model="U">
  </range-slider>
</div>      

<button class="run" @click="Close()">Закрыть</button>

<div class="block">
Мощность на валу электродвигателя <br>{{kVt}} кВт
    <range-slider
    class="slider"
    min="1"
    max="4"
    step="1"
    v-model="kVt">
  </range-slider>
</div>

<p class="run">Статус:{{status}}</p>

<p style="color:green;">{{info}}</p>

<div class="block">

Номинальный ток <br>{{I}},0 А
   <range-slider
    class="slider"
    min="1"
    max="10"
    step="1"
    v-model="I">
  </range-slider>
</div>



<button class="run" @click="Run()">Открыть</button>

<div class="block">
Скорость вращения<br>{{V}} об/мин.
   <range-slider
    class="slider"
    min="0"
    max="5500"
    step="500"
    v-model="V">
  </range-slider>
</div>

<div class="block">
Частота, регулируемая электронным блоком <br>{{Gz}} Гц.
   <range-slider
    class="slider"
    min="0"
    max="650"
    step="50"
    v-model="Gz">

  </range-slider>
</div>
<br>
<!-- - номинальное напряжение питания – трехфазное 380 В ±10%, диапазон регулирования (65 – 110) % Uном;

- мощность на валу электродвигателя – 3 кВт;

- номинальный ток Iном = 7,0 А, диапазон изменения (0…10) А ±10 %, скорость вращения – 5000 об/мин, диапазон изменения (0…5500) об/мин.

- частота, регулируемая электронным блоком в диапазоне 0 – 650 Гц. -->


</main>
</div>
</template>

<script>

import RangeSlider from 'vue-range-slider'
import 'vue-range-slider/dist/vue-range-slider.css'
import { fail } from 'assert';

export default {
  data () {
    return {
      U: 50,
      kVt:2,
      I:1,
      V:500,
      Gz:0,
      status:false,
      info:""
    }
  },
  components: {
    RangeSlider
  },
  methods:{
      Run(){
        if(this.status===true){
          this.info = "Ворота и так открыты!"
        }
        else if(this.U===100 && this.kVt ===3 && this.I === 7 && this.V===5000 &&  this.Gz ===450){
          this.status = true
          this.info = "Ворота открыты!"
        }else{
          this.info = "Не удалось открыть ворота"
        }
      },
      Close(){
        if(this.status===false){
          this.info = "Ворота и так закрыты"
        }else{
            this.info = "Ворота закрылись"
            this.status = false
        }

      }
  }
}
</script> 
 
<style>

.status{
  
}
.exit{
    margin-top:200px;
}
.run{
    margin-top:200px;
}

.slider {
  /* overwrite slider styles */
  width: 200px;
}
.block {
margin-left: 100px;
}

/*Button Exit*/
a.bot1{
    background:linear-gradient(to bottom, #FFFFFF, #E6E6E6) #F5F5F5 repeat-x;
    border-color: rgba(0, 0, 0, 0.1) rgba(0, 0, 0, 0.1) #B3B3B3;
    border-radius: 4px;
    border-style: solid;
    border-width: 1px;
    box-shadow: 0 1px 0 rgba(255, 255, 255, 0.2) inset, 0 1px 2px rgba(0, 0, 0, 0.05);
    color: #333333;
        text-decoration:none;
    display:block;
    font-size: 14px;
        width:120px;
    line-height: 20px;
    margin: 20px auto;
    padding: 4px 12px;
    text-align: center;
    text-shadow: 0 1px 1px rgba(255, 255, 255, 0.75);
    vertical-align: middle;
  position: relative;
  -webkit-transition-duration: 0.3s;
  transition-duration: 0.3s;
  -webkit-transition-property: -webkit-transform;
  transition-property: transform;
  -webkit-tap-highlight-color: rgba(0, 0, 0, 0);
  -webkit-transform: translateZ(0);
  -ms-transform: translateZ(0);
  transform: translateZ(0);
  box-shadow: 0 0 1px rgba(0, 0, 0, 0);
}

a.bot1:before {
  pointer-events: none;
  position: absolute;
  z-index: -1;
  content: '';
  top: 100%;
  left: 5%;
  height: 10px;
  width: 90%;
  opacity: 0;
  background: -webkit-radial-gradient(center, ellipse, rgba(0, 0, 0, 0.35) 0%, rgba(0, 0, 0, 0) 80%);
  background: radial-gradient(ellipse at center, rgba(0, 0, 0, 0.35) 0%, rgba(0, 0, 0, 0) 80%);
  -webkit-transition-duration: 0.3s;
  transition-duration: 0.3s;
  -webkit-transition-property: -webkit-transform, opacity;
  transition-property: transform, opacity;
}

a.bot1:hover {
  -webkit-transform: translateY(-5px);
  -ms-transform: translateY(-5px);
  transform: translateY(-5px);
}
a.bot1:hover:before {
  opacity: 1;
  -webkit-transform: translateY(5px);
  -ms-transform: translateY(5px);
  transform: translateY(5px);
}
</style> 