<template>
    <div>
        <div id="treeheader" v-on:mouseover="mouseOver" v-on:mouseout="mouseOut">
            <img src="../assets/left.png" height="10" width="10"> 
            <img src="../assets/folder.png" height="10" width="12">
            {{nodedata["head"].name}}
        </div>
        <folder id="head" v-bind:nodedata="nodedata"></folder>
    </div>
  
</template>

<script>
import folder from "./folder.vue"

export default {
    name: "treeheader",
    components:{folder},
    props:[
        "id",
        "nodedata"
    ],
    methods:{
        mouseOver : function (event){
            document.querySelector("#treeheader").style.backgroundColor = "grey"
        },
        mouseOut : function(event){
            document.querySelector("#treeheader").style.backgroundColor = "white"
        }
    }

}
</script>

<style>

</style>