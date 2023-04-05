<template>
<div class="text">
  <h1> 3. Inverse modulaire </h1>
    <h2> 3.1 Définition </h2>
          <p> L'inverse modulaire est un chiffre, "i", qui, combiné à un autre chiffre "a", vaut 1 mod n. "i" peut aussi être noté comme étant congru modulo à "a" puissance "-1" mod n.</p>
          <p> 3.1.1 Exemples de notation </p>
          <p> a * u ≡ 1 mod n </p>
          <p> u ≡ a^-1 mod n</p>
    <h2> 3.2 Prérequis </h2>
        <h3> 3.2.1 PGDC </h3>
          <p> Le PGDC entre a et u doit être égal à 1 pour qu'ils soient premiers entre eux. Si il n'est pas égal à 1 a et u ne sont pas premiers entre eux et l'inverse n'éxiste pas.</p>
        <h3> 3.2.2 Exemple de calcul </h3>
          <p> u ≡ 4^-1 mod 19 </p>
          <p> On commence par chercher le PGDC de 4 et 19 </p>
          <p> PGDC(19;4) = 1, il existe donc un inverse </p>
          <p> u ≡ 4^-1 mod 19, on passe le 4^-1 de l'autre coté </p>
          <p> 4 * u ≡ 1 mod 19, on remplace le calcul en équation </p>
          <p> 4 * u = 19 + 1, on trouve que u vaut 5</p>
          <p> 5 ≡ 4^-1 mod 19 </p>
    <h2> 3.3 Algorithme d'Euclide </h2>
        <h3> 3.3.1 Définition </h3>
          <p> La formule de l’algorithme d'Euclide est "a*u + b*v = PGDC(a;b)". Dans cette formule ont connaît "a" et "b" et on cherche "u" et "v".</p>
        <h3> 3.3.2 Résoudre mathématiquement </h3>
          <p> En prenant l'équation "a*u + n*v = 1" et "a*u + b*v = PGDC(a;b)" on peut trouver "u" et "v" où "n" est le modulo, "a" et "b" sont des chiffres connus. Si PGDC(a;n) = 1, on peut faire le calcul. Il suffit ensuite de remplacer les valeurs et le faire.</p>
        <h3> 3.3.3 Résoudre avec le tableau </h3>
          <p>Le tableau permet de trouver l'inverse par étape. Chaque étape s'approche de plus en plus du "u" et "v" recherché.</p>
        <h3> 3.3.4 Le tableau </h3>    
</div>

<Tableauinverse>

</template>

<script>
import Tableauinverse from './Tableauinverse.vue'

export default {
  name: 'Texteinverse',
  components: {
    Tableauinverse
  },
  data(){
    return{
      text: ["modulo", "chiffre", "q", "s", "t", "Reste"],
      text_right: [-49.5, -37, -23.5, -5, 24, 40.5],
      colonne_right: ["12","23","32","60","89","101"]
    }
  },
  methods: {
    range(k) {
      let result = Array(k);
      for (let i = 0; i < k; i++) {
        result[i] = i;
      }
      return result;
    },
}}
</script>

<style>
.text {
  color: #D9D9D9
}
</style>