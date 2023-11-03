<script setup>
  import {ref} from "vue";
  let note = ref('');
  let notes = ref([])
  let noteMoyenne = ref()
  function addNote() {
    const parsedNote = parseFloat(note.value);
    if (!isNaN(parsedNote) && parsedNote > 0 && parsedNote <= 6) {
      notes.value.push(parsedNote);
      console.log(note.value)
    }
  }


  function calculMoyenne() {
    let sum = 0;
    for (let i = 0; i < notes.value.length; i++) {
      sum += notes.value[i];
    }
    const count = notes.value.length;
    noteMoyenne.value = count > 0 ? sum / count : 0;
    console.log(noteMoyenne)
  }

</script>

<template>
  <div style="display: grid">
    <h1>Calculer sa moyenne de math</h1>
    <input ref="input" v-model="note">
    <button v-on:click="addNote">Ajouter une note</button>
    <button v-on:click="calculMoyenne">Calculer la moyenne</button>
    <h2>{{notes}}</h2>
    <h2>Moyenne : {{ Math.round(noteMoyenne * 10) / 10 }}</h2>
  </div>

</template>

<style scoped>
div {
  text-align: center;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  padding: 20px;
  background-color: #f0f0f0;
  border-radius: 10px;
  box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.2);
  font-family: Arial, sans-serif;
}

h1 {
  font-size: 24px;
  color: #333;
  margin-bottom: 20px;
}

input {
  padding: 10px;
  margin-right: 10px;
  border: 1px solid #ccc;
  border-radius: 5px;
}

button {
  padding: 10px 20px;
  background-color: #007BFF;
  color: #fff;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  margin: 10px;
}

button:hover {
  background-color: #0056b3;
}

h2 {
  font-size: 20px;
  color: #333;
  margin-top: 20px;
}
</style>