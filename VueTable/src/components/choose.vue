<template>
    <div id="selectArea">
        <div class="tips">
            <ul>
                <li v-show="checkedNames1" v-on:click="cancel(1)">
                    <span>变更中</span>
                    <img src="../assets/cancel.png" alt="" class="cancel">
                </li>
                <li v-show="checkedNames2" v-on:click="cancel(2)">
                    <span>未生效</span>
                    <img src="../assets/cancel.png" alt="" class="cancel">
                </li>
                <li v-show="checkedNames3" v-on:click="cancel(3)">
                    <span>作废</span>
                    <img src="../assets/cancel.png" alt="" class="cancel">
                </li>
                <li v-show="checkedNames4" v-on:click="cancel(4)">
                    <span>正常</span>
                    <img src="../assets/cancel.png" alt="" class="cancel">
                </li>
                <li v-show="checkedNames5" v-on:click="cancel(5)">
                    <span>审核中</span>
                    <img src="../assets/cancel.png" alt="" class="cancel">
                </li>
            </ul>
            <img src="../assets/show.png" alt="" v-on:click="show()">
        </div>
        <div class="select" v-if="IsShow">
            <input type="search" class="search">
            <div class="check">
                <input type="checkbox" id="jack" value="1" v-model="checkedNames1" class="selected">
                <label for="jack">变更中</label>
            </div>
            <div class="check">
                <input type="checkbox" id="john" value="2" v-model="checkedNames2" class="selected">
                <label for="john">未生效</label>
            </div>
            <div class="check">
                <input type="checkbox" id="mike" value="3" v-model="checkedNames3" class="selected">
                <label for="mike">作废</label>
            </div>
            <div class="check">
                <input type="checkbox" id="mike" value="4" v-model="checkedNames4" class="selected">
                <label for="mike">正常</label>
            </div>
            <div class="check">
                <input type="checkbox" id="mike" value="5" v-model="checkedNames5" class="selected">
                <label for="mike">审核中</label>
            </div>     
        </div>
    </div>
</template>

<script>
import axios from 'axios'
    export default {
      name: 'tableElem',
      data() {
        return {
          checkedNames: "",
          IsShow:true,
          checkedNames1:false,
          checkedNames2:false,
          checkedNames3:false,
          checkedNames4:false,
          checkedNames5:false,
          choices:[
              {index:1,value:"变更中"},
              {index:1,value:"未生效"},
              {index:1,value:"作废"},
              {index:1,value:"正常"},
              {index:1,value:"审核中"}
          ]
        }
      },
      methods:{
         show(){
             this.IsShow = !this.IsShow;
         },
         cancel(value){
             if(value == 1){
                 this.checkedNames1 = false;
             }else if(value == 2){
                 this.checkedNames2 = false;
             }else if(value == 3){
                 this.checkedNames3 = false;
             }else if(value == 4){
                 this.checkedNames4 = false;
             }else if(value == 5){
                 this.checkedNames5 = false;
             }
         }
      }
    }
  </script>
  <style>
  ul li{
      float:left;
      margin:0;
      padding:0;
      list-style: none;
  }
  ul{
      width:500px;
      height:50px;
      float:left;
  }
  li{
      border:1px solid #ddd;
      height:30px;
      line-height:30px;
      padding-left:20px;
      border-radius: 30px;
      background-color:#d2d2d3;
  }
  .tips{
      width:600px;
      height:50px;
      border:1px solid #ddd;
  }
  .cancel{
      width:40px;
      height:30px;
  }
  img{
      width:50px;
      height:50px;
      float:right;
  }
  .select{
      width:600px;
      height:400px;
      border:1px solid #ddd;
  }
  .search{
      width:570px;
      height:40px;
      margin-top:5px;
      margin-left:7px;
      border-radius: 35px;
      border:1px solid #ddd;
  }
  .selected{
      width:25px;
      height:25px;

  }
  label{
      font-size:25px;
  }
  .check{
      margin-top:10px;
      margin-left:30px;
      text-align: left;
  }
  </style>
  

  