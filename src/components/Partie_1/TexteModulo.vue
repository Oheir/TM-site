<template>
  
<div class="text">
  <h1 > 1. La congruence modulaire </h1>
    <h2> 1.1 Qu'est ce que c'est? </h2> 
        <p> La congruence modulaire est une division entière entre un nombre, nommé "a", et un modulo, nommé "n". Le résultat de cette division est nommé "b".</p>
      <h3> 1.1.1 L'horloge </h3>
        <p>La congruence modulaire peut être vue comme un horloge. Dans cette horloge "a" est l'heure, par exemple 16h, "b" l'heure indiquée par l'horloge, ici 4h, et "n" le nombre d'heures sur l'horloge.</p>
    <h2 > 1.2 Notation </h2>
        <p> La congruence est noté de plusieurs manières. La plus commune est la notation de Gauss. Elle est notée "a ≡ b mod n". "a" et "b" sont "congrus modulo n". </p>
      <h3> 1.2.1 Exemples de notation de Gauss: </h3>
        <p> 24 ≡ 4 mod 10 </p>
        <p> 12 ≡ 0 mod 12 </p>
        <p> 9 ≡ 3 mod 6 </p>
      <h3> 1.2.2 "≡" </h3>
        <p> Le signe "≡" réprésente la congruence modulo. Il ne représente pas le même concept que"="". Cependant, il peut être remplacé par "=" avec un autres type de notation. </p>
      <h3> 1.2.3 Notation avec "=" </h3>
        <p>La notation de Gausse peut être remplacé par une équation. La forme de cette notation est "a = b + k*n". Dans cette notation "k" est le nombre de "tours" nécessaire pour obtenir "a".</p>
      <h3> 1.2.4 Exemples d'équations: </h3>
        <p> 24 = 4 + 2 * 10 </p>
        <p> 12 = 12 * 1 </p>
        <p> 9 = 3 + 6 * 1 </p>
      <h3>1.2.5 Notation dans un code</h3>
        <p> "%" est le signe utilisé pour la congruence modulaire en informatique. Ce signe représente la même chose que "≡" mais renvoie le "b". </p>
        <p> Exemples: </p>
        <p> 24 % 10 = 4 </p>
        <p> 12 % 12 = 0 </p>
        <p>  9 % 6 = 3 </p>
    <h2> 1.3 Propriétés </h2>
        <p> Réflexivité:</p>
        <p>Prenez un "a" qui est entier et il sera toujours congru modulo à lui même.</p>
        <p> Symétrie:</p>
        <p> Pour "a" et "b" des nombres entiers. Si "a" est congru modulo à "b" alors l'inverse est vrai.</p>
        <p> Transivité:</p>
        <p> Prenez "a", "b" et "c" qui sont tous des nombres entiers. Si "a" est congru modulo "b" qui est congru modulo "c" alors "a" est congru modulo "c".</p>
      <h3> 1.3.1 Exemples: </h3>
        <p> Refléxivité: 4 ≡ 4 mod 10</p>
        <p> Symétrie: 15 ≡ 3 mod 12 donc 3 ≡ 15 mod 12</p>
        <p> Transivité: 25 ≡ 15 mod 10, 15 ≡ 5 mod 10 alors 25 ≡ 5 mod 10 </p>
  <h2> 1.4 Exemple interactif </h2>
      <h3> 1.4.1 Comment utiliser l'horloge </h3>
        <p> La barre au dessus de l'horloge permet choisir le modulo "n". La roue représente tout les "b" possibles dans le modulo "n". Cliquez sur le cercle pour choisir le "b". La barre montre tout les "a" congrus modulo à "b". 
        <p> </p>
  <h3> 1.4.2 L'horloge </h3>
  <Cercle>

</div>
</template>

<script>
import Cercle from './Cercle.vue'

export default {
  name: 'Textecongruence',
  components: {
    Cercle
  },
  data() {
    return {

    };
  },
  computed: {
    calcul_mod() {
      let a  = []
      let b = []
      let mod = []
      let mod_n = 0
      let a_n = 0

      for (let i = 0; i < 10; i++){
        a_n = Math.floor(Math.random()*30)
        mod_n = Math.floor(Math.random()*30)

        b.push(b)
        a.push(a)
        mod.push(mod_n)
        
     } 
     return [a,b,mod]
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
  color: #D9D9D9
}
.text {
  color: #D9D9D9
}

</style>
