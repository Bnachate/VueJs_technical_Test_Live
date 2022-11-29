<template>
    <h1>Profil</h1>
    <input
      v-model="userName"
      style="background-color: #e4e4e4; border: 1px solid #000000;"
      type="text"
    />
    <p v-if="error" style="color: red">this user doesn't exist</p>
    <button
    @click="getUser"
      style="background-color: #e4e4e4; border: 1px solid #000000;"
    >
      See
    </button>
      <h2>{{ results.login }}</h2>
      <h3>{{ results.created_at }}</h3>
      <img :src="results.avatar_url" />
</template>
<script>
export default {
    emits: ['get-user-request'],
    props: ['results', 'error'],
    data() {
        return {
            userName: '',
        };
    },
    methods: {
        getUser() {
            this.$emit('get-user-request', this.userName);
        }
    }
}
</script>