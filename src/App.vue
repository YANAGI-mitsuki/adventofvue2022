<script setup>
import { ref, computed } from 'vue';

const keyword = ref ('');
const users = ref([
    {
        id: 1,
        name: '鈴木太郎',
        email: 'suzukitaro@example.com'
    },
    {
        id: 2,
        name: '佐藤二郎',
        email: 'satoujiro@example.com'
    },
    {
        id: 3,
        name: '田中三郎',
        email: 'tanakasaburo@example.com'
    },
    {
        id: 4,
        name: '山本四郎',
        email: 'yamamotoshiro@example.com'
    },
    {
        id: 5,
        name: '高橋五郎',
        email: 'takahashigoro@example.com'
    }
  ]);
  const filteredUsers = computed(() => {
      const filteredUsers = [];

      for (const user of users.value) {
        if (user.name.includes(keyword.value) || user.email.includes(keyword.value)) {
          filteredUsers.push(user);
        }
      }

      return filteredUsers;
    });

</script>

<template>
  <div id="app">
    <input type="text" v-model="keyword">
    <table>
        <tr v-for="user in filteredUsers" :key="user.id">
            <td v-text="user.id"></td>
            <td v-text="user.name"></td>
            <td v-text="user.email"></td>
        </tr>
    </table>
</div>
</template>

<style scoped>

</style>
