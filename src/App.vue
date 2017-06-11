<template>
    <div id="app">
        <img src="./assets/logo.png">
        <h1>{{msg | uppercase}}</h1>
        <h2>Essential Links</h2>
        <ul>
            <li><a href="https://vuejs.org" target="_blank">Core Docs</a></li>
            <li><a href="https://forum.vuejs.org" target="_blank">Forum</a></li>
            <li><a href="https://gitter.im/vuejs/vue" target="_blank">Gitter Chat</a></li>
            <li><a href="https://twitter.com/vuejs" target="_blank">Twitter</a></li>
        </ul>
        <h2 v-bind:title="firstName + ' ' + lastName ">Ecosystem</h2>
        <h3>{{age}}</h3>
        <h3>{{ age < 1000 ? 'Less Than 1000' : 'More than 1000'}}</h3>
        <h3 v-if="!fullName.isEmpty">{{fullName}}</h3>
        <button @click="alertFunction">Click me</button>
        <button @click="multiply">Multiply age</button>
        <button @click="getFullName">Full Name</button>
        <button @click="clickedButton">Button for me</button>
        <button @click="change=!change">Change color</button>
        <a v-bind:href="url">Google</a>
        <br>
        <input type="text" v-model="firstName"><br>
        <div v-html="html"></div>
        <br>
        <br>
        <ul>
            <li><a href="http://router.vuejs.org/" target="_blank">vue-router</a></li>
            <li><a href="http://vuex.vuejs.org/" target="_blank">vuex</a></li>
            <li><a href="http://vue-loader.vuejs.org/" target="_blank">vue-loader</a></li>
            <li><a href="https://github.com/vuejs/awesome-vue" target="_blank">awesome-vue</a></li>
        </ul>
        <br><br><br><br>
        <p v-if="amount > 20">If Items inn stock > 20</p>
        <p v-else-if="amount > 10">If items is stock > 10</p><br>
        <p> Else amount </p><br><br>
        <input type="text" v-model="amount"><br><br><br><br>
        <ul>
            <li v-bind:style="{'background-color': change ? 'red' : 'blue'}" v-for="fruit in fruits">{{fruit}}</li>
        </ul>
        <ul>
            <li v-for="(employee, index) in employees">{{index}}.{{employee.name}}</li>
        </ul>
        <ul>
            <li v-for="employee in employees">
                <p v-for="(value, key) in employee">
                    <span>{{key}}: {{value}}</span>
                </p>
            </li>
        </ul>
        <ul>
            <li v-for="i in 10">{{i}}</li>
        </ul>
        <br>
        <input type="text" v-model="value" @keyup.enter="addEmployee(value)">
        <div v-bind:style="{'background-color': color}">
            <p>Color</p>
            <p>Color</p>
            <p>Color</p>
            <p>Color</p>
        </div>
        <input type="text" v-model="color">
    </div>
</template>

<script>
    export default {
        name: 'app',
        data () {
            return {
                msg: 'Welcome to Your Vue.js App',
                age: 26,
                firstName: 'Zmitser',
                lastName: 'Koskinen',
                fullName: '',
                url: "http://vk.com",
                html: '<p>Hello Zmitser Barysavets</p>',
                amount: 1,
                fruits: ["Banana", "Orange", "Apple", "Mango"],
                employees: [
                    {name: 'Zmitser', title: 'Accountant'},
                    {name: 'Kirill Polsky', title: 'Administrative Worker'},
                    {name: 'Mikhail Goncharov', title: 'Botanist'},
                    {name: 'Igor Krasheninnikov', title: 'Carpenter'},
                    {name: 'Alexander Dedyulya', title: 'Composer'},
                    {name: 'Tatyana Egortseva ', title: 'Diver'}
                ],
                value: '',
                change: true,
                color: 'red'

            }
        },
        methods: {
            alertFunction () {
                alert('Hello!')
            },
            multiply () {
                this.age *= 3
            },
            getFullName () {
                this.fullName = this.firstName + ' ' + this.lastName
            },
            clickedButton () {
                alert("Clicked button!")
            },
            addEmployee (value) {
                this.fruits.push(value)
            }
        },
        filters: {
            uppercase (msg) {
                return msg.toString().toUpperCase()
            }
        }
    }
</script>

<style>
    #app {
        font-family: 'Avenir', Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #2c3e50;
        margin-top: 60px;
    }

    h1, h2 {
        font-weight: normal;
    }

    ul {
        list-style-type: none;
        padding: 0;
    }

    li {
        display: inline-block;
        margin: 0 10px;
    }

    a {
        color: #42b983;
    }
</style>
