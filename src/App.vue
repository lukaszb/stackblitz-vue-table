<script setup lang="ts">
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://vuejs.org/api/sfc-script-setup.html#script-setup
import { ref } from "vue";
import Table from "./components/Table.vue";
import Column from "./components/Column.vue";

const data = [
  {
    id: "1",
    name: "Kate Brown",
    age: 32,
    address: "New York No. 1 Lake Park",
    tags: ["nice", "developer"],
  },
  {
    id: "2",
    name: "Jane Doe",
    age: 34,
    address: "London No. 1 Lake Park",
    tags: ["engineer"],
  },
  {
    id: "3",
    name: "Joe Black",
    age: 32,
    address: "Sidney No. 1 Lake Park",
    tags: ["cool", "teacher"],
  },
];
</script>

<template>
  <h3>Table:</h3>
  <Table :data="data">
    <Column header="id">
      <template v-slot="{ item }">
        {{ item.id }}
      </template>
    </Column>
    <Column>
      <template #header><strong>Name</strong></template>
      <template v-slot="{ item }">
        {{ item.name }}
      </template>
    </Column>
    <Column header="Address">
      <template v-slot="{ item }">
        {{ item.address }}
      </template>
    </Column>
  </Table>
  <hr />

  <h3>Raw data:</h3>
  <pre
    style="
      text-align: left;
      padding: 12px;
      border-radius: 5px;
      background-color: black;
      color: limegreen;
      font-size: 14px;
    "
    >{{ JSON.stringify(data, null, 2) }}</pre
  >
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
