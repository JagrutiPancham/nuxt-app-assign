<template>
    <div>
        <nav class="flex items-center justify-between flex-wrap bg-blue-700 p-6">
    <div class="flex items-center flex-shrink-0 text-white mr-6">
        <span class="font-semibold text-xl tracking-tight">Welcome!!</span>
    </div>
        <div>
        <a href="#" class="flex justify-endinline-block text-sm px-4 py-2 leading-none border rounded text-white border-white hover:border-transparent hover:text-teal-500 hover:bg-white mt-4 lg:mt-0"><nuxt-link to="Login">Logout</nuxt-link></a>
        </div>
    </nav>
        <div class="mx-3 my-2">
            <br/>
            <h6 align="center">Please choose items to your bucket</h6>
            <div class="grid grid-cols-3 gap-2 mt-14">
                <div class="p-6 max-w-sm bg-red-400 rounded-lg border border-gray-200 shadow-md dark:bg-gray-800 dark:border-gray-700">
                    <div class="mb-2 text-2xl text-center font-bold tracking-tight text-gray-900 dark:text-white">{{ apple.name }}</div>
                    <div class="flex flex-1 justify-center p-9 text-4xl">{{ apple.count }}</div>
                    <div class="flex flex-1 justify-center"><button v-on:click="add" class="py-2 px-4 rounded-full h-14 w-14 bg-white text-black mx-1">+</button><button v-on:click="remove" class="py-2 px-4 rounded-full h-14 w-14 bg-white text-black mx-1">-</button></div>
                </div>
                <div class="p-6 max-w-sm bg-green-300 rounded-lg border border-gray-200 shadow-md dark:bg-gray-800 dark:border-gray-700">
                    <div class="mb-2 text-2xl text-center font-bold tracking-tight text-gray-900 dark:text-white">{{ orange.name }}</div>
                    <div class="flex flex-1 justify-center p-9 text-4xl">{{ orange.count }}</div>
                    <div class="flex flex-1 justify-center"><button @click="add1" class="py-2 px-4 rounded-full h-14 w-14 bg-white text-black mx-1">+</button><button v-on:click="remove1" class="py-2 px-4 rounded-full h-14 w-14 bg-white text-black mx-1">-</button></div>
                </div>
                <div class="p-6 max-w-sm bg-blue-400 rounded-lg border border-gray-200 shadow-md dark:bg-gray-800 dark:border-gray-700">
                    <div class="mb-2 text-2xl text-center font-bold tracking-tight text-gray-900 dark:text-white">{{ grapes.name }}</div>
                    <div class="flex flex-1 justify-center p-9 text-4xl">{{ grapes.count }}</div>
                    <div class="flex flex-1 justify-center"><button v-on:click="add2" class="py-2 px-4 rounded-full h-14 w-14 bg-white text-black mx-1">+</button><button
                            v-on:click="remove2" class="py-2 px-4 rounded-full h-14 w-14 bg-white text-black mx-1">-</button></div>
                </div>
            </div>
        </div>
        <div class="m-8">
            <div class="mx-34">
                <h4 align="center"><b><u>Basket stack</u></b></h4>
            </div>
            <div>
            <center>
            <table class="w-64  items-center justify-center"><tr class="border-solid border-2 border-black-600 w-10" v-for="(basket, index) in basket.slice().reverse()" :key="index">
            <td :class="bckg[basket]">{{basket}}</td>
            </tr></table>
            </center>
            </div>
        </div>
    </div>
</template>

    <script>
   export default {
    data() {
        return {
            
            "apple": {
                name: "Apple",
                count: 10,
                color: ""
            },
            "orange": {
                name: "Orange",
                count: 10,
                color: ""
            },
            "grapes": {
                name: "Grapes",
                count: 10,
                color: ""
            },
            basket: [],
            bckg:{
                "Apple": 'app',
                "Orange": 'ora',
                "Grapes": 'gra'
            }
        }
    },
    methods: {
        add() {
            if (this.apple.count > 0) {
                this.apple.count = this.apple.count === 0 ? 0 : this.apple.count - 1;
                this.basket.push(this.apple.name)
            }
            else {
                alert("you already aaded 10 item")
            }
        },
        remove() {
            if (this.basket.at(-1) == this.apple.name) {
                this.apple.count = this.apple.count === 10 ? 10 : this.apple.count + 1;
                this.basket.pop()
            }
            else {
                alert("Invalid item ")
            }
        },
        add1() {
            if (this.orange.count > 0) {
                this.orange.count = this.orange.count === 0 ? 0 : this.orange.count - 1;
                this.basket.push(this.orange.name)
            }
            else {
                alert("You have selected 10 items")
            }
        },
        remove1() {
            if (this.basket.at(-1) == this.orange.name) {
                this.orange.count = this.orange.count === 10 ? 10 : this.orange.count + 1;
                this.basket.pop()
            }
            else {
                alert("Invalid item ")
            }
        },
        add2() {
            if (this.grapes.count > 0) {
                this.grapes.count = this.grapes.count === 0 ? 0 : this.grapes.count - 1;
                this.basket.push(this.grapes.name)
            }
            else {
                alert("You have selected 10 items ")
            }
        },
        remove2() {
            console.warn(this.basket.at(-1))
            if (this.basket.at(-1) == this.grapes.name) {
                this.grapes.count = this.grapes.count === 10 ? 10 : this.grapes.count + 1;
                this.basket.pop()
            }
            else {
                alert("Innvalid item ")
            }
        },
    }
}
    </script>
    <style scoped>
    .app{
         background-color: rgb(248 113 113);
         /* red 400 */
    }
    .ora{
        background-color: rgb(134 239 172);
        /* green 300 */
    }
    .gra{
        background-color: rgb(96 165 250);
        /* blue 400 */
    }
    </style>