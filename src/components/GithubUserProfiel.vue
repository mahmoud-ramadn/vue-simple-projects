<script setup>
import { ref } from 'vue';

const username = ref('');
const userprofile = ref(null);
const erro = ref(null);

const getUserProfile = async () => {
    try {
        const res = await fetch(
            `https://api.github.com/users/${username.value}`
        );

        const data = await res.json();

        if (res.ok) {
            userprofile.value = data;
            erro.value = null;
        } else {
            userprofile.value = null;
            erro.value = `Error: ${data.message}`;
        }
    } catch (error) {
        console.error('Error fetching data', error);
        erro.value = 'An error occurred while fetching data.';
    }
};

console.log(userprofile.value);

</script>

<template>
  <div class="github-profile-viewer">
    <h1 class="app-title">GitHub User Profile Viewer</h1>

    <div class="input-container">
      <input
        v-model="username"
        placeholder="Enter GitHub username"
        
      />

      <button @click="getUserProfile" >search</button>
    </div>

    <div v-if="userprofile" class="user-profile">
      <img :src="userprofile.avatar_url" :alt="userprofile.login" />
      <div class="user-details">
        <p><strong>Name:</strong> {{ userprofile.login }}</p>
        <p><strong>Location:</strong> {{ userprofile.location }}</p>
        <p><strong>Followers:</strong> {{ userprofile.followers }}</p>
        <p><strong>Following:</strong> {{ userprofile.following }}</p>
        <p><strong>Public Repos:</strong> {{ userprofile.public_repos }}</p>
      </div>
    </div>

    <div v-if="erro" class="error-message">
      <p>{{ erro }}</p>
    </div>
  </div>
</template>

<style scoped>
.github-profile-viewer {
  max-width: 600px;
  margin: 50px auto;
  padding: 20px;
  text-align: center;
  border: 1px solid #ccc;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.app-title {
  font-size: 24px;
  margin-bottom: 20px;
  color: #333;
}

.input-container {
  margin-bottom: 20px;
}

input {
  width: 100%;
  padding: 10px;
  font-size: 16px;
}

.user-profile {
  margin-top: 20px;
}

h2 {
  font-size: 20px;
  margin-bottom: 10px;
  color: #333;
}

img {
  width: 150px;
  border-radius: 50%;
  margin-bottom: 20px;
}

.user-details {
  text-align: left;
}

p {
  font-size: 16px;
  margin-bottom: 10px;
}

.error-message {
  color: #e74c3c;
  margin-top: 20px;
}
</style>
