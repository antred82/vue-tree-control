<template>
  <div class="mytreelist">
      <nav class="menu">
          <table>
              <tr class="menubar">
                  <td class="menutitle">File list</td>
                  <td class="newFolderCol"><img class="newFolder" src="../assets/folder_new.png" height="25" width="25" @click="makeNewFolder"></td>
                  <td class="newFileCol"><img class="newFile" src="../assets/file_new.png" height="25" width="25"></td>
              </tr>
          </table>
      </nav>
      <section>
        <!--<ul class="folder" id="head" >
            <li><img src="../assets/left.png" height="10" width="10">test<ul class="folder"><li> ttt </li></ul></li>
        </ul>-->
        <treeheader v-bind:nodedata="nodedata"></treeheader>
      </section>
  </div>
</template>

<script>
import treeheader from "./header.vue"

export default {
    components:{treeheader},

    mounted: function(){
        var self = this
        self.drawTreeControl()
        window.addEventListener("resize",function(){
            //console.log("resized")
            self.drawTreeControl()
        })
        var new_folder = document.querySelector(".newFolder")
        new_folder.addEventListener("mousedown", function(event){
            new_folder.src = require("../assets/folder_new_click.png")
            //console.log("mouse down new folder")
        })

        new_folder.addEventListener("mouseup", function(event){
            new_folder.src = require("../assets/folder_new.png")
            //console.log("mouse up new folder")
        })

        var new_file = document.querySelector(".newFile")
        new_file.addEventListener("mousedown", function(event){
            new_file.src = require("../assets/file_new_click.png")
            //console.log("click new file")
        })

        new_file.addEventListener("mouseup", function(event){
            new_file.src = require("../assets/file_new.png")
            //console.log("click new file")
        })

    },
    methods:{
        drawTreeControl:function(){
            var treeListObj = document.querySelector(".mytreelist")
            this.listWidth = treeListObj.offsetWidth
            this.listHeight = treeListObj.offsetHeight
        },
        makeNewFolder: function(){

        }
    },
    data: function(){
        return {
            listWidth : 0,
            listHeight : 0,
            curSelNode: "head",
            nodedata:{
                "head":{type:"folder",name:"test",url:"./",isShow:true, parent:"",child:["test2","test3"]},
                "test2":{type:"folder", name: "hello", url:"./test",isShow:true, parent:"head",child:["test4"]},
                "test3":{type:"file", name: "hello.cpp", url:"./test",isShow:true, parent:"head",child:[]},
                "test4":{type:"file", name: "test.cpp", url:"./test",isShow:true, parent:"test2",child:[]}
            }
        }
    }
}
</script>

<style>
select.itemList{
    -webkit-appearance: none;
    font-size: 16px;
    font-family: 맑은고딕;
    border-top-width: 0px;
    border-bottom-width: 0px;
}

ul.folder{
    list-style-type: none;
    text-align: left;
    padding-inline-start: 10px;
    margin-block-start: 3px;
}

li{
    margin-block-start: 3px;
}

table{
    width: 100%;
    background-color: darkgrey
    
}

td.menutitle{
    text-align: left;
    padding-left: 10px;
}

td.newFolderCol{
    width: 30px;
    text-align: center;
    padding-left: 1px;
}
td.newFileCol{
    width: 30px;
    text-align: center;
    padding-left: 1px;
}

</style>