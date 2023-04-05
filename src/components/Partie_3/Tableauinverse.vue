<template>
  <div class="input_layout">
    <input class="input" v-model="a">
    <input class="input" v-model="b"> 
  </div>
  
  <svg :viewBox="'0 0 100 100'" xmlns="http://www.w3.org/2000/svg">
    <rect x="0" y="0" width="100" height="10" 
    style="fill: #D9D9D9; stroke: black; stroke-width: 0.5"/>
    <g v-for="i in range(6)">
     <line :x1=colonne_right[i] y1="-50" :x2=colonne_right[i] :y2=(10*(step+1))
     style="stroke: black; stroke-width: .3"/>     
     <text 
        x="50"
        y="50"
        fill="black"
        font-size="20%"
        :transform="`translate(${text_right[i]} -44)`">
        {{text[i]}}
      </text>
      </g>
    <g v-for="i in range(step)"
        font-size="20%"
        fill=" #D9D9D9">
      <text 
      x="50"
      y="50"
      :transform="`translate(${text_right[0] + 2} ${-33 + 10*i})`">
        {{remplissage_calcul[0][i + 1]}}
      </text>
      <text 
      x="50"
      y="50"
      :transform="`translate(${text_right[1] + 2} ${-33 + 10*i})`">
        {{remplissage_calcul[1][i + 1]}}
      </text>
       <text 
      x="50"
      y="50"
      :transform="`translate(${text_right[2]} ${-33 + 10*i})`">
        {{remplissage_calcul[2][i + 1]}}
      </text>
       <text 
      x="50"
      y="50"
      font-size="70%"
      :transform="`translate(${text_right[3] - 10} ${-33 + 10*i})`">
        {{remplissage_equ[0][i + 1]}}
      </text>
       <text 
      x="50"
      y="50"
      font-size="70%"
      :transform="`translate(${text_right[4] - 10} ${-33 + 10*i})`">
        {{remplissage_equ[1][i + 1]}}
      </text>
       <text 
      x="50"
      y="50"
      :transform="`translate(${text_right[5] + 2} ${-33 + 10*i})`">
        {{remplissage_calcul[3][i + 1]}}
      </text>
    </g>
    <text v-if="remplissage_calcul[3][step] != 0 ">
    </text>
    <text
    x="25"
    y="100"
    font-size="20%"
    fill="#D9D9D9"
    v-else>
    inverse modulaire = {{remplissage_equ[2]}} + {{a}} = {{remplissage_equ[3]}}
    </text>
  </svg>

  <div class="input_layout">
    <button class="input" v-if="remplissage_calcul[3][step] != 0 " @click="step++">prochaine étape</button>
    <button class="input" v-else>prochaine étape</button>
    <button class="input" v-if="step > 0" @click="step--">étape précédente</button>
    <button class="input" v-else>étape précédente</button>
  </div>

</template>

<script>
export default {
  name: 'Tableauinverse',
  props: {
    msg: String
  },
  data() {
    return {
      a: 167,
      b:23,
      step: 0,
      text: ["modulo", "chiffre", "q", "s", "t", "Reste"],
      text_right: [-49.5, -37, -23.5, -5, 24, 40.5],
      colonne_right: ["12","23","32","60","89","101"]
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
    remplissage_calcul() {
      let a = this.a
      let b = this.b
      let reste = 0
      let quo = 0

      let quo_arr =[0]
      let reste_arr = [1]
      let a_arr = [0]
      let b_arr = [0]

      for (let i = 0; i < this.step + 1; i++){
        quo = Math.floor(a/b)
        reste = a - b * quo

        a_arr.push(a)
        b_arr.push(b)
        quo_arr.push(quo)
        reste_arr.push(reste)

        a = b
        b = reste
      }
      return [a_arr,b_arr,quo_arr,reste_arr]
    },
    remplissage_equ(){
      let a = this.a
      let b = this.b
      let quo = 0
      let reste = 0
      let longueur = 0
      let inverse = 0

      let s_arr = [0]
      let t_arr = [0]
      let s_arr_number = [0]
      let t_arr_number = [1]

      for (let i = 0; i < this.step ; i++){
        quo = Math.floor(a / b)
        reste = a - b * quo
        
        if(i == 0){
          s_arr.push(1)
          t_arr.push(-quo)
          t_arr_number.push(-quo)
          s_arr_number.push(1)
        }
        else{
          t_arr_number.push(t_arr_number[i-1] - quo * t_arr_number[i])
          s_arr_number.push(s_arr_number[i-1] - quo * s_arr_number[i])

          s_arr.push(`${s_arr_number[i-1]} - ${quo} * ${s_arr_number[i]} = ${s_arr_number[i+1]}` )
          t_arr.push(`${t_arr_number[i-1]} - ${quo} * ${t_arr_number[i]} = ${t_arr_number[i+1]}`)
        }
        a = b
        b = reste
        inverse = t_arr_number[t_arr_number.length - 2] 
        inverse += parseInt(this.a)
      }
      return [s_arr,t_arr,t_arr_number[t_arr_number.length - 2], inverse]
    }
  }
}
</script>

<style>
.input_layout{
  margin-bottom:20px;
  display:flex;
  justify-content: space-around;
  margin-top: 40px
}
.input{
  border-radius: 5px;
  background-color: #D9D9D9;
}
</style>
