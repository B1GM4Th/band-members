<script setup>
import { ref } from 'vue';

const listMembers = ref([])

const newMember = ref({
  nome: '',
  sobrenome: '',
  instrumento: '',
})

const addNewMember = () => {
  if(newMember.value.nome && newMember.value.sobrenome && newMember.value.instrumento)
  listMembers.value.push(newMember.value)
  newMember.value = {}
}
const excludeMember = (item) => {
  const i = listMembers.value.indexOf(item)
  if(i > -1) {
    listMembers.value.splice(i, 1)
  }
}
</script>

<template>
  <main>
    <h1>Membros da Banda</h1>

    <table>
      <thead>
        <tr>
          <th>Nome</th>
          <th>Sobrenome</th>
          <th>Instrumento</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="member in listMembers">
          <td>{{ member.nome }}</td>
          <td>{{ member.sobrenome }}</td>
          <td>{{ member.instrumento }}</td>
          <td @click="excludeMember(member)">X</td>
        </tr>
      </tbody>
    </table>

    <section>
      <p>Adicionar membros</p>
      <form>
        <label for="fname">Nome</label>
        <input type="text" name="fname" id="fname" v-model="newMember.nome">

        <label for="lname">Sobrenome</label>
        <input type="text" name="lname" id="lname" v-model="newMember.sobrenome">

        <label for="instrument">Instrumento</label>
        <select name="instrument" id="intrument" v-model="newMember.instrumento">
          <option value="Baixo">Baixo</option>
          <option value="Guitarra">Guitarra</option>
          <option value="Bateria">Bateria</option>
          <option value="Violão">Violão</option>
          <option value="Flauta">Flauta</option>
          <option value="Violino">Violino</option>
        </select>

        <input type="button" value="Adicionar" @click="addNewMember()">
      </form>
    </section>
  </main>
</template>

<style></style>