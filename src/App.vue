<script setup></script>

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
        <tr>
          <td>nome</td>
          <td>sobrenome</td>
          <td>instrumento</td>
        </tr>
      </tbody>
    </table>

    <section>
      <p>Adicionar membros</p>
      <form>
        <label for="fname"></label>
        <input type="text" name="fname" id="fname">

        <label for="lname"></label>
        <input type="text" name="lname" id="lname">

        <select name="instrument" id="intrument">
          <option value="Baixo">Baixo</option>
          <option value="Guitarra">Guitarra</option>
          <option value="Bateria">Bateria</option>
          <option value="Baixo">Violão</option>
          <option value="Baixo">Flauta</option>
          <option value="Baixo">Violine</option>
        </select>

        <input type="button" value="Adicionar" @click="[]">
      </form>
    </section>
  </main>
</template>

<style></style>