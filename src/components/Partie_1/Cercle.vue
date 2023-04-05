<template>
  <input v-model.number="k" placeholder="edit me" />
  
  <svg viewBox="0 0 100 100" xmlns="http://www.w3.org/2000/svg">
    <g>
      <circle cx="50" cy="20" r="10" />
    </g>
    <g fill="#D9D9D9">
      <circle cx="50" cy="20" r="9.7" />
    </g>
    <g
      v-for="i in range(k)"
      key="i"
      fill="#3500D3"
      :transform="`rotate(${angle_generator[i]} 50 20) translate(0 -20)`"
    >
      <circle cx="50" cy="50" :r="angle_gen[i]" @click="count=id_generator[i], mod_n=id_generator[i], rayon_spec=id_generator[i] "/>
      <text
        x="50"
        y="50"
        fill="white"
        font-size="20%"
        :transform="`rotate(0 50 50) translate(-1 5)`"
      >
        {{ id_generator[i] }}
      </text>
    </g>
  </div>
  <line x1="10" y1="50" x2="90" y2="50" stroke="#D9D9D9" />
  <g
      v-for="i in range(5)"
    :transform="`translate(${-30 + 15*i} 0)`"
      fill="#3500D3"
    >
      <circle cx="50" cy="50" r="2" @click="mod_n=number_gen[i]"/>
        <text
        x="50"
        y="50"
        fill="white"
        font-size="20%"
        :transform="`translate(-1 5)`"
      >
        {{ number_gen[i] }} 
      </text>
      </g>
    <g>
  </svg>
  <div class="btn">
      <svg width="37" height="52" viewBox="0 0 37 52" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path d="M0.998413 25.5965L26.5934 51.1914L36.1915 41.5933L20.1946 25.5965L36.1915 9.59963L26.5934 0.00152588L0.998413 25.5965Z" fill="#D9D9D9" @click="mod_k--"/>
      </svg>

        
      <svg width="37" height="52" viewBox="0 0 37 52" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path d="M0.998413 41.5933L10.5965 51.1914L36.1915 25.5965L10.5965 0.00152588L0.998413 9.59963L16.9953 25.5965L0.998413 41.5933Z" fill="#D9D9D9" @click="mod_k++"/>
      </svg>

  </div>
<p id="ca">{{mod_n}} ≡ {{count}} (mod {{k}})</p>

</template>

<script>
export default {
  name: 'Cercle',
  props: {
    msg: String
  },
  data() {
    return {
      i: '',
      k: 12,
      count: 0,
      mod_k: 1,
      mod_n: 0,
      rayon_spec: 0  
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
    angle_generator() {
      let n = 1;
      let nbr_angle_base = 360 / this.k;
      let nbr_angle = 360 / this.k;
      let angles = [180];

      while (n < this.k) {
        angles.push(180 + nbr_angle);
        nbr_angle += nbr_angle_base;
        n++;
      }

      return angles;
    },
    id_generator() {
      let id = [0];
      let n = 1;

      while (n < this.k) {
        id.push(n);
        n++;
      }
      return id;
    },
    number_gen() {
      let mod_k = this.mod_k;
      let count = this.count;
      let k = this.k
      let nums = []
  

      for (let i = -3; i < 2; i++){
         nums.push(count + k * (mod_k + i))
      }
      
      return nums 
    },
    angle_gen() {
      let rayons = []
      let rayons_spec = this.rayon_spec
      let n = 0
      while(n < this.k){
        if(n == rayons_spec){
          rayons.push(2)
        }
        else{
          rayons.push(1.5)
        }
        n++
      }
      return rayons
    }

      
    
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
#a {
  transform-origin: 50% 50%;
}
.btn{
  transform: translate(0px, -400%);
  display: flex;
  justify-content: space-around;

}
#ca{
  color: #D9D9D9;
  transform: translate(0px, -350px);
}
</style>
