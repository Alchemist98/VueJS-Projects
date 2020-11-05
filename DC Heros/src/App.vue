<template>
<AppHeader />
<div class="w-full flex">
    <div class="m-auto">
        <h1 class="text-3xl text-center">DC heroes</h1>
        <ul>
            <li class="flex justify-between" v-for="(hero, index) in dcHeroes" :key="hero.name">
                <div>
                    {{ hero.name }}
                </div>
                <button v-on:click="remove(index)">x</button>
            </li>
        </ul>
        <form class="mt-10" @submit.prevent="addHero">
            <input class="border rounded" v-model.trim="newHero" placeholder="Type Hero Name" />
            <button class="border rounded bg-gradient-to-r from-red-700 to-pink-500 text-white" type="submit">Add Hero</button>
        </form>
        <span>Number of superheroes: {{ heroCount }}</span>
    </div>
</div>
</template>

<!--<button :disabled="isDisabled">Add Hero</button>
<br>
<a :href="link">YouTube</a>-->
<!--v-model and it required data field through which you're going to connect the v-model-->
<!--each element of array(dcHeroes) is object so i need to create an object with a key name -->
<!--The this keyword within Vue gives you easy access to all of your data and functionalities.
Wether you want to access a data property,a computed property, a component prop or a function,
you can all find them directly on the this keyword. he reason behind it is to simplify
the access to all of your different data in the instance.-->

<script>
import AppHeader from "./components/AppHeader";
export default {

    components: {
        AppHeader
    },

    computed: {
        heroCount() {
            return this.dcHeroes.length;
        },
    },

    methods: {
        addHero() {
            if (this.newHero != "") {
                this.dcHeroes.unshift({
                    name: this.newHero,
                });
                this.newHero = "";
            }
        },

        remove(index) {
            this.dcHeroes.splice(index, 1);
        },
    },

    data() {
        return {
            newHero: "",
            dcHeroes: [{
                    name: "SuperGirl",
                },
                {
                    name: "Batman",
                },
                {
                    name: "Flash",
                },
                {
                    name: "Arrow",
                },
                {
                    name: "Superman",
                },
            ],
        };
    },
};
</script>

<style>
</style>
