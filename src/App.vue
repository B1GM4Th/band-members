<script setup>
import { ref } from 'vue';
import { Icon } from '@iconify/vue';

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
          <td @click="excludeMember(member)" class="cursor-pointer"><Icon icon="line-md:close-small" /></td>
        </tr>
      </tbody>
    </table>

    <section class="add-members">
      <p>Adicionar membros</p>
      <form>
        <label for="fname">Nome:</label>
        <input type="text" name="fname" id="fname" v-model="newMember.nome">

        <label for="lname">Sobrenome:</label>
        <input type="text" name="lname" id="lname" v-model="newMember.sobrenome">

        <label for="instrument">Instrumento:</label>
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

<style>
body {
  @apply flex justify-center w-screen h-screen bg-blue-300
}

main {
  @apply w-fit flex flex-col items-center mt-32
}

h1 {
  @apply text-3xl font-bold p-5
}

td {
  @apply text-center
}

main td, main th {
  @apply p-2 border-collapse;
}

main th {
  @apply border-b
}

.add-members {
  @apply flex flex-col items-center m-10 p-6 bg-gray-200 w-[80vw]
}

.add-members p {
  @apply text-lg
}

.add-members form {
  @apply flex flex-col gap-2 p-6
}

.add-members form input {
  @apply w-[10vw] px-2
}

.add-members form input[type='button'] {
  @apply bg-blue-300 mt-4 p-1
}

.add-members form input[type='button']:hover {
  @apply bg-blue-400
}
</style>