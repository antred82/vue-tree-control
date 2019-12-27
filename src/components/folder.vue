<template>
    <ul class="folder" v-bind:id="id">
        <li v-bind:class="nodedata[child].type" v-bind:key="child" v-for="child in nodedata[id].child">
            <template v-if="nodedata[child].type==='file'">
                <!--<img src="../assets/left.png" height="10" width="10">-->{{nodedata[child].name}}
            </template>
            <template v-if="nodedata[child].type==='folder'">
                <img src="../assets/left.png" height="10" width="10">
                <img src="../assets/folder.png" height="10" width="12"> {{nodedata[child].name}}
                <template v-if="nodedata[child].child.length > 0">
                    <folder v-bind:id="child" v-bind:nodedata="nodedata"></folder>
                </template>
            </template>
        </li>
    </ul>
  
</template>

<script>
export default {
    name: "folder",
    //components:{"folderObj": folderObj},
    props:[
        "id",
        "nodedata"
    ]

}
</script>

<style>

</style>