<template lang="html">
<div id="app">
    <div class="inner" v-bind:style="{gridTemplateRows:rowNo}">
        <div class="rows" v-for="(row,rowindex) in rows" v-bind:style="{gridTemplateColumns:columnNo}">
            <div 
              v-for="(column, columnindex) in columns"
              v-bind:class="{ column: !true, columns: obe[rowindex+"."+ columnindex] }" >
              {{}}
              </div>
        </div>
    </div>
    <div class="inner">
       <div class="lower-rows" v-for="(row,rowindex) in rows" v-bind:style="{gridTemplateColumns:columnNo}">
            <div 
            class="lower-columns" 
            v-for="(column, columnindex) in columns"
        
              v-on:click="clicked(rowindex, columnindex )"/>
            </div>
        </div>
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
        rowNo: "",
        look: "",
        obe:{},
        columnNo: "",
        rows: [1, 2, 3,4, 5],
        columns: [1, 2, 3,4, 5]
    }),
    created() {
        this.call();
    },
    methods: {
        clicked(rowIndex, columnIndex){
          this.obe[rowIndex+"."+columnIndex] = false
          console.log(this.obe)
        },
        call() {
            if (this.columnNo === "") {
                this.columns.forEach(() => {
                    this.columnNo = this.columnNo + " 1fr"
                })
            }
            if (this.rowNo === "") {
                this.rows.forEach((row, rowIndex) => {
                    this.rowNo = this.rowNo + " 1fr"
                    this.columns.forEach((column, columnIndex) => {
                        this.obe[rowIndex+"."+columnIndex] = true
                    })
                })
            }
            console.log(this.obe)
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
    background: #212121;
    grid-template-rows: 1fr 1fr;
    grid-gap: 15px;
}

.inner {
    background: #212121;
    display: grid;
    height: 100%;
    width: 100%;
}
.inner:first-child {
    background: #212121;
    display: grid;
    height: 100%;
    width: 100%;

}

.rows {
    background: #97217d;
    display: grid;
}
.lower-rows {
    background: #97217d;
    display: grid;
}

.columns {
    background: #219774;
    border: 2px solid #cec7c7;
}

.column {
    background-image: url("./assets/X.png");
    border: 2px solid #cec7c7;
    background-size: 100%;
}
.lower-columns{
    background: #217f97;
    border: 2px solid #cec7c7;
}
</style>
