<template>
    <div id="app">
        <h1>On {{date}} it is {{villager.gender == 'Male' ? '♂' : '♀'}} {{villager.name['name-USen']}}s birthday!</h1>
        <img id="image" :src="villager.image_uri">

        <br>
        <h2>Personality: {{villager.personality}}</h2>
        <h2>Catchphrase: {{villager['catch-phrase']}}</h2>
    </div>
</template>

<script>
const _ = require('lodash')

import date from 'date-and-time'
const villagers = require('./assets/villagers.json')

let todayDate

function findBirthday(bday) {
    for (const key in villagers) {
        const subObject = villagers[key]

        if (subObject['birthday'] === bday) {
            return subObject
        }
    }
}

export default {
    mounted() {
        
    },
    data() {
        const today = new Date()
        todayDate = date.format(today, 'D/M')

        return {
            date: todayDate,
            villager: findBirthday(todayDate)
        }
    }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Itim&display=swap');

* {
    padding: 5px;
    margin: 0px;
}

@import './assets/style.css';
</style>