<template>
  <div class="container">
    <h1>Calculateur IMC</h1>
    <p>Taille (en cm)</p>
    <input type="text" id="taille">

    <p>Poids (en kg)</p>
    <input type="text" id="poids">

    <button id="btn">Calculer</button>
    <div id="resultat"></div>
  </div>
</template>

<script setup>
window.onload = () => {
  let button = document.querySelector("#btn");
  button.addEventListener("click", calculateIMC);
};
  
function calculateIMC() {
  let taille = parseInt(document.querySelector("#taille").value);
  let poids = parseInt(document.querySelector("#poids").value);

  let resultat = document.querySelector("#resultat");
  if (taille === "" || isNaN(taille)) 
    resultat.innerHTML = "Indiquer une taille valide!";

  else if (poids === "" || isNaN(poids)) 
    resultat.innerHTML = "Indiquer un poids valide!";
  else {
    let imc = (poids / ((taille * taille)/ 10000)).toFixed(2);
    if (imc < 18.6) resultat.innerHTML = `Sous poids : <span>${imc}</span>`;

    else if (imc >= 18.6 && imc < 24.9) resultat.innerHTML = `Normal : <span>${imc}</span>`;
    else resultat.innerHTML = `En surpoids : <span>${imc}</span>`;
  }
}
</script>
