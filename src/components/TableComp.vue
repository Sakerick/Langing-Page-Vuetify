<template>
  <v-table class="w-100 ma-auto" striped="even" style="width:120%; max-width:900px;">
    <thead>
      <tr>
        <th class="text-left">
          Name
        </th>
        <th class="text-left">
          Calories
        </th>
        <th>
          Price
        </th>
      </tr>
    </thead>
    <tbody>
      <tr
        v-for="item in desserts"
        :key="item.name"
      >
        <td>{{ item.name }}</td>
        <td>{{ item.calories }}</td>
        <td>{{ item.price }}</td>
      </tr>
    </tbody>
  </v-table>
</template>

<script lang="ts" setup>
  const desserts = [
    {
      name: 'Frozen Yogurt',
      calories: 159,
      price: 20,
    },
    {
      name: 'Ice cream sandwich',
      calories: 237,
      price: 15,
    },
    {
      name: 'Eclair',
      calories: 262,
      price: 25,
    },
    {
      name: 'Cupcake',
      calories: 305,
      price: 12,
    },
    {
      name: 'Gingerbread',
      calories: 356,
      price: 7,
    },
  ]
</script>
