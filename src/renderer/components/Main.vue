<template>
<div>
<main>



<div class="chunky1"><a href="/">Выход</a></div>

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
        this.info = ""
        this.status = false
        if(this.U===100 && this.kVt ===3 && this.I === 7 && this.V===5000 &&  this.Gz ===450){
          this.status = true
          this.info = "Ворота открыты!"
        }else{
          this.info = "Не удалось открыть ворота"
        }
      },
      Close(){
        this.info = "Ворота закрылись"
        this.status = false
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
</style> 