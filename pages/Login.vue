<template>
<div class="flex items-center justify-center min-h-screen bg-gray-100">
    <div class="px-8 py-6 mt-4 text-left bg-gray-400 shadow-lg">
        <p class="text-2xl font-bold m-5 ">
            Login
        </p>
        <div>
            <input v-model="username" type="text" placeholder="User Name" class="text-sm text-gray-base w-full mr-3 py-5 px-4 h-2 border border-gray-200 rounded mb-2" />
            <input v-model="password" type="password" placeholder="Password" class="text-sm text-gray-base w-full mr-3 py-5 px-4 h-2 border border-gray-200 rounded mb-2" />
           
            <div class="flex justify-center border-black">
                <button @click="login" class="shadow bg-purple-100 hover:bg-grey-1000 focus:shadow-outline 
                     focus:outline-none text-black border-black font-bold py-2 px-4 rounded">
                        <NuxtLink to ="/bucket">Submit</NuxtLink>
                </button>
            </div>
            <div>
                <NuxtLink to="/signUp" >
               <h1 class="text-white ">Register</h1>
                </NuxtLink>
            </div>
        </div>
    </div>
</div>
</template>

<script>
import axios from "axios"
export default {
    name: "login",
    data() {
        return {
            username: "",
            password: ""
        }
    },
    methods: {
        async login() {
            let result = await axios.get(
                `http://localhost:3000/users?username=${this.username}&password=${this.password}`
            );
            if (result.status == 200 && result.data.length > 0) {
                this.$router.push({
                    name: "bucket"
                })
            } else {
                alert("please enter correct username and password")
                // sadfsdfgbfds
                // asdfggit
            }
        }
    }
}
</script>
