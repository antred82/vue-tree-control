<template>
    <div id="treeheader">
        <img src="../assets/left.png" height="10" width="10"> 
        <img src="../assets/folder.png" height="10" width="12">
        {{nodedata["head"].name}}
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
    ]

}
</script>

<style>

</style>