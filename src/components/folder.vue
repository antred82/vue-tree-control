<template>
    <ul class="folder" v-bind:id="id">
        <li v-bind:class="nodedata[child].type" v-bind:key="child" v-for="child in nodedata[id].child">
            <template v-if="nodedata[child].type==='file'">
                <div v-bind:id="child" @mouseover="mouseOver($event,child)" @mouseout="mouseOut($event,child)" @click="fileItemClick($event,child)">
                <!--<img src="../assets/left.png" height="10" width="10">-->{{nodedata[child].name}}
                </div>
            </template>
            <template v-if="nodedata[child].type==='folder'">
                <div v-bind:id="child" @mouseover="mouseOver($event,child)" @mouseout="mouseOut($event,child)" @click="folderItemClick($event,child)">
                    <img v-bind:src="FolderShowImage" height="10" width="10">
                    <img src="../assets/folder.png" height="10" width="12"> {{nodedata[child].name}}
                </div>
                <template v-if="nodedata[child].child.length > 0 && nodedata[child].isShow === true">
                    <folder v-bind:id="child" v-bind:nodedata="nodedata" v-bind:callback="callback"></folder>
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
        "nodedata",
        "callback"
    ],
    methods:{
        mouseOver : function (event,i_id){
            document.querySelector("#"+i_id).style.backgroundColor = "grey"
        },
        mouseOut : function(event,i_id){
            document.querySelector("#"+i_id).style.backgroundColor = "white"
        },
        folderItemClick: function(event, i_id){
            if(this.nodedata[i_id].isShow === true){
                this.FolderShowImage = require("../assets/down.png")
            }
            else{
                this.FolderShowImage = require("../assets/left.png")
            }
            this.nodedata[i_id].isShow = !this.nodedata[i_id].isShow
            this.nodedata["lastSelKey"] = i_id
        },
        fileItemClick: function(event, i_id){
            this.callback(this.nodedata[i_id],i_id)
            this.nodedata["lastSelKey"] = i_id
        }
    },
    data:function(){
        return {
            FolderShowImage: require("../assets/left.png")

        }
    }

}
</script>

<style>

</style>