<template>
  <div class="input_layout">
    <input class="input"v-model="a" placeholder="a">
    <input class="input"v-model="b" placeholder="b"> 
  </div>
  <div id="ad">
    <svg viewBox="0 0 100 100" xmlns="http://www.w3.org/2000/svg">
    <rect x="0" y="0" width="100" height="10" 
    style="fill: #D9D9D9; stroke: black; stroke-width: 0.5"/>
    <g v-for="i in range(6)" >
     <line :x1=colonne_right[i] y1="-50" :x2=colonne_right[i] :y2=(10*(longueur+1))
     style="stroke: black; stroke-width: .3"/>     
     <text 
        x="50"
        y="50"
        fill="black"
        font-size="20%"
        :transform="`translate(${text_right[i]} -44)`"
        fill="#D9D9D9">
        {{text[i]}}
      </text>
      </g>
    <g v-for="i in range(longueur)"
        font-size="20%"
        fill="#D9D9D9">
      <text 
      x="50"
      y="50"
      :transform="`translate(${text_right[0] + 2} ${-33 + 10*i})`">
        {{i + 1}}
      </text>
      <text 
      x="50"
      y="50"
      :transform="`translate(${text_right[1] + 2} ${-33 + 10*i})`">
        {{remplissage_calcul[0][i]}}
      </text>
       <text 
      x="50"
      y="50"
      :transform="`translate(${text_right[2] + 2} ${-33 + 10*i})`">
        {{remplissage_calcul[1][i]}}
      </text>
       <text 
      x="50"
      y="50"
      font-size="70%"
      :transform="`translate(${text_right[3] - 4} ${-33 + 10*i})`">
        {{remplissage_calcul[2][i]}}
      </text>
       <text 
      x="50"
      y="50"
      :transform="`translate(${text_right[4] + 2} ${-33 + 10*i})`">
        {{remplissage_calcul[3][i]}}
      </text>
       <text 
      x="50"
      y="50"
      :transform="`translate(${text_right[5] + 2} ${-33 + 10*i})`">
        {{remplissage_calcul[4][i]}}
      </text>
    </g>
  </div>
  </svg>

  <div class="input_layout">
    <button  class="input" v-if="step < longueur" @click="step++">prochaine étape</button>
    <button  class="input" v-else>prochaine étape</button>
    <button  class="input" v-if="step > 0" @click="step--">étape précédente</button>
    <button  class="input" v-else>étape précédente</button>
  </div>
</template>

<script>
export default {
  name: 'Tableaupdgc',
  props: {
    msg: String
  },
  data() {
    return {
      a: '',
      b:'',
      step: 0,
      text: ["étape", "Dividende a", "Diviseur b", "équation", "Quotient", "Reste"],
      text_right: [-48, -37, -16, 5, 24, 40.5],
      colonne_right: ["12","32","50","72","89","101"]
    };
  },
  methods: {
    range(k) {
      let result = Array(k);
      for (let i = 0; i < k; i++) {
        result[i] = i;
      }
      return result;
    },
  },
  computed: {
    longueur() {
      let a = this.a;
      let b = this.b;
      let t = 0
      let i = 0

      while(b!=0){
        t = b
        b = a % b
        a = t
        i ++
        }
      i++
      return i
    },
    remplissage_calcul() {
      let a_arr = []
      let b_arr = []
      let equ_arr = []
      let quo_arr = []
      let res_arr = []

      let a = this.a
      let b = this.b
      let quo = 0
      let reste = 0      
      
        for (let i = 0; i < this.step; i++){
           if(b!=0){
            quo = Math.floor(a/b)
            reste = a-(b*Math.floor(a/b))

            a_arr.push(a)
            b_arr.push(b)
            quo_arr.push(quo)
            res_arr.push(reste)
            equ_arr.push(`${a} = ${b} * ${quo} + ${reste}`)

            a = b
            b = reste
            
          }
          else{
            a_arr.push(a)
            b_arr.push(b)
            equ_arr.push(`pgdc = ${a}`)
          }
        }
       return [a_arr,b_arr,equ_arr,quo_arr,res_arr]
     
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
},
#ad{
  background:white
}
.input_layout{
  margin-bottom:20px;
  display:flex;
  justify-content: space-around;
}
.input{
  border-radius: 5px;
  background-color: #D9D9D9;
}
</style>