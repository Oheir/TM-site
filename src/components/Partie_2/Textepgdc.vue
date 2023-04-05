<template>
<div class="text">
  <h1>2. Plus Grand Diviseur Commun</h1>
    <h2> 2.1 Définition </h2>
        <p> Le Plus Grand Diviseur Commun de plusieurs nombres est le plus grand nombre permettant donnant un nombre entier avec une division.</p>
      <h3> 2.1.1 Exemples </h3>
        <p> Le Plus Grand Diviseur Commun de 10 et 20 est 10.</p>
        <p> Car 10 / 10 = 1 et 20 / 10 = 2. Il n'y a pas de plus grand nombre permettant d'avoir une division donnant un nombre entier que 10.</p>
        <p> Le Plus Grand Diviseur Commun de 8 et 4 est 4.</p>
        <p>Le Plus Grand Diviseur Commun de 3 et 2 est 1.</p>
        <p>Le Plus Grand Diviseur Commun de 25 et 5 est 5.</p>
    <h2> 2.2 Écriture </h2>
        <p> Le PGDC s'écrit PGDC(a;b), "a" et "b" sont des nombres entiers. Le PGDC n'est pas limité à 2 nombres, il peut aussi être noté PGDC(a;b;c).</p>
      <h3> 2.2.1 Exemples </h3>
        <p> Le PGDC de 10 et 20 s'écrit : PGDC(20;10) = 10. </p>
        <p> PGDC(8;4) = 4</p>
        <p> PGDC(3;2) = 1</p>
        <p> PGDC(25;5) = 5</p>
    <h2> 2.3 Résolution </h2>
        <p> Il y a plusieurs moyens de trouver le PGDC de 2 nombres. </p>
      <h3> 2.3.1 Méthode des diviseurs</h3>
        <p> La méthode des diviseurs consiste à faire une liste de tous les diviseurs des nombres choisis. Regarder quel sont les diviseurs communs et en prendre le plus grand. Cette méthode est facile à faire mais prends du temps si les nombres sont trop grands.</p>
        <p> Exemple: </p>
        <p> a = 20, b = 46, c = 34 </p>
        <p> PGDC(20;46;34) = </p>
        <p> diviseurs a = {1,2,4,5,10,20}</p>
        <p> diviseurs b = {1,2,23,46}</p>
        <p> diviseurs c = {1,2,17,34}</p>
        <p> diviseurs communs = {1,2}</p>
        <p> PGDC(20;46;34) = 2</p>
      <h3> 2.3.2 Méthode des nombres premiers</h3>
        <p> La méthode des nombre premiers cherche le PGDC en divisant les 2 nombres par des nombres premiers en même temps. Il faut ensuite multiplier les nombres trouvés. Cette méthode est meilleure pour des nombres plus grands.</p>
        <p> Exemple: </p>
        <p> a = 144, b = 258 </p>
        <p> PGDC(144;258) = </p>
        <p> nombre premier = 2, a = 72; b = 129 </p>
        <p> nombre premier = 3, a = 24; b = 43 </p>
        <p> 43 est un nombre premier. On ne peut plus diviser. </p>
        <p> PGDC(144;258) = 2 * 3 = 6 </p>
      <h3> 2.3.3 Méthode des facteurs communs</h3>
        <p> La méthode des facteurs communs consiste à décomposer les nombres en facteurs premiers. Ensuite, il faut regarder les nombres qu'ils ont en communs, ceux qui ne le sont pas ne servent pas dans cette méthode. Pour finir, il suffit de les multiplier.</p>
        <p> Exemple: </p>
        <p> a = 68, b = 94 </p>
        <p> PGDC(68;94) = </p>
        <p> a = 2 * 2 * 17 </p>
        <p> b = 2 * 47 </p>
        <p> PGDC(68;94) = 2 </p>
    <h2> 2.4 Algorithme d'Euclide </h2>
      <h3> 2.4.1 Prérequis </h3>
        <p> Les nombres "a" est "b" doivent être positifs.</p>
        <p> PGDC(a;b) = PGDC(a-b;b) </p>
        <p> Quand "b" vaut zéro, "a" est le PGDC </p>
      <h3> 2.4.2 Fonctionnement </h3>
        <p> On prend les 2 nombres "a" et "b". On fait une division entière entre les 2. Elle nous donne notre quotient. Ce quotient sert à déterminer le reste entre les 2 nombres. On peut trouver le reste grâce au quotient, ou en cherchant "a" modulo "b". "a" devient "b" et "b" prends la valeur du "reste". </p>
      <h3> 2.4.3 Exemple </h3>
        <p> a = 54, b = 8 </p>
        <p> PGDC(54;8) = </p>
        <p> 54 % 8 = 6, reste = 6</p>
        <p> On fait les changements de valeurs: a = b = 8, b = reste = 6</p>
        <p> 8 % 6 = 2, reste 2 </p>
        <p> On fait les changements de valeurs: a = b = 6, b = reste = 2</p>
        <p> 6 % 2 = 0, reste 0</p>
        <p> Le reste vaut zéro. Comme le PGDC est a: PGDC = 6</p>
      <h3> 2.4.4 Tableau </h3>
        <p> Le tableau permet de visualer toutes ces étapes. Vous pouvez choisir les valeurs de "a" et "b" grâce aux "inputs" ci-dessous. Cliquer ensuite sur "prochaine étape" ou "étape précédente" pour naviguer le tableau</p>
</div>
<Tableaupgdc>
</template>

<script>
import Tableaupgdc from './Tableaupgdc.vue';

export default {
  name: 'Textepgdc',
  components: {
    Tableaupgdc,
  },

};
</script>

<style>
.text {
  color: #d9d9d9;
}
</style>
