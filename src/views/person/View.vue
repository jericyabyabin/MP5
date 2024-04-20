<template>
  <h1>Person</h1>
  <table class="table table-hover">
    <thead>
      <tr>
        <th scope="col">#</th>
        <th scope="col">ID</th>
        <th scope="col">Yearly Income</th>
        <th scope="col">Address</th>
        <th scope="col">Birthdate</th>
        <th scope="col">Years of Education</th>
        <th scope="col">Age</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="(person, index) in persons" :key="person.id">
        <th scope="row">1</th>
        <td>{{ person.id }}</td>
        <td>{{ person.yearlyIncome }}</td>
        <td>{{ person.address }}</td>
        <td>{{ person.birthDate }}</td>
        <td>{{ person.yearsEdu }}</td>
        <td>{{ person.age }}</td>
        <td>
          <RouterLink :to="{ path: '/person/${person.id}/update'}" class'>
        </td>
      </tr>
    </tbody>
  </table>
</template>

<script setup>
import axios from "axios";
import { onMounted, ref } from "vue";
import { RouterLink } from "vue-router";

const persons = ref([]);

onMounted(() => {
  axios
    .get("http://localhost/MP5_Yabyabin/backend/personapi.php?action=get_all")
    .then((error) => {
      persons.value = response.data;
    })
    .catch((error) => {
      console.error("Error fetching data", error);
    });
});
</script>
