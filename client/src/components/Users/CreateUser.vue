<template>
    <div>
        <h1>Create User</h1>
        <form v-on:submit.prevent = "createUser">
            <p>name: <input type="text" v-model="user.name"></p>
            <p>lastname: <input type="text" v-model="user.lastname"></p>
            <p>email: <input type="text" v-model="user.email"></p>
            <p>password: <input type="text" v-model="user.password"></p>
            <button type="submit">create user</button>
            <button v-on:click="navigateTo('/users/')">back</button>
        </form>
    </div>
</template>
<script>
import UsersService from '../../services/UsersService';

    export default {
        data () {
            return {
                user: {
                    name: '',
                    lastname: '',
                    email: '',
                    password: '',
                    status: 'active',
                }
            }
        },
        methods: {
            async createUser () {
                try {
                    await UsersService.post(this.user)
                    this.$router.push({
                        name: 'users'
                    })
                }catch (error) {
                    console.log(error)
                }
            }
        }
    }
</script>
<style scoped>
   h1{
        color: blue;
    }
    p{
        color: rgb(161, 161, 247);
    }
</style>

