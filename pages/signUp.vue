<template>
<div flex items-center justify-center min-h-screen bg-gray-100>
    <h1>Register</h1>
    <form method="post">
        <input type="text" placeholder="User name" v-model="username" id="name"><br>

        <input type="password" placeholder="Password" v-model="password" id="password"><br>

        <button type="submit" @click="signUp"><NuxtLink to="Login">Submit</NuxtLink></button>
    </form>
</div>
</template>

<script>
import axios from 'axios'
export default {
    name:"sign",
    data()
    {
        return {
            username:'',
            password:'',
        }
    },
    methods:{
        async signUp(){
            console.warn("this is called",this.username,this.password)
            let result= await axios.post("http://localhost:3000/users",
                {
                    username:this.username,
                    password:this.password
                })
            console.warn(result)
            if(result.status==201){
                alert("You are registerd!")
            }
}
    }
}
</script>

<style scoped>
div {
    text-align: center;
    width: 100%;
    margin: 0 auto;
    padding: 0px;
    background-color:white;
}

input[type=text],
input[type=password] {
    background-color: rgb(241, 245, 247);
    width: 20%;
    padding: 12px 20px;
    border-radius: 4px;
    margin: 8px 2px;
    display: inline-block;
    border: 1px solid rgb(17, 17, 17);
    box-sizing: border-box;
}

button {
    background-color: skyblue;
    color: white;
    padding: 14px;
    margin: 2px;
    border: 1px solid rgb(17, 17, 17);
    cursor: pointer;
    width: 20%;

}
</style>
