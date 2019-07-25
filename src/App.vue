<template lang="html">
<div id="app">
    <div class="inner" v-bind:style="{gridTemplateRows:back}">
        <div v-for="row in rows" class="rows" />
    </div>
    <div class="inner">
        <button v-on:click="rows">call</button>
    </div>
</div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
    name: 'app',
    components: {
        HelloWorld
    },
    data: () => ({
        back: "",
        rows: [1, 2, 3],
        column: [1, 2, 3, 4, 5]
    }),
    methods: {
        rows(){
          this.rows.forEach(row =>{
            this.back = this.back + " 1fr"
          })
        },
        call() {
            alert("call")
            $value = "1fr";
        }
    }
}
</script>

<style>
* {
    padding: 0px;
    margin: 0px;
}

#app {
    height: 100vh;
    width: 100vw;
    display: grid;
    grid-template-rows: 1fr 1fr;
}

.inner {
    background: #212121;
    display: grid;
    height: 100%;
    width: 100%;
    /* grid-template-rows: 1fr 1fr 1fr; */
}

.rows {
    background: #97217d;
}
</style>
