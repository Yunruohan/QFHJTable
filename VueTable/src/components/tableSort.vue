<template>
    <el-table
      :data="tableData"
      style="width: 20%;margin:0 auto;border:1px solid #ddd;">
      <el-table-column
        prop="name"
        label="姓名"
        width="180">
      </el-table-column>
      <el-table-column
        prop="age"
        label="年龄"
        width="180">
      </el-table-column>
    </el-table>
  </template>

  <script>
  import { Table,TableColumn } from 'element-ui'
  import axios from 'axios'
    export default {
      name: 'tableElem',
      data() {
        return {
          tableData: []
        }
      },
      mounted() {
         this.getData();
      }, 
      methods:{
        getData(){
          axios.get('https://api.myjson.com/bins/19gaco').then( (res) =>{
              let table = res.data;
              this.tableData = table.sort(function(a,b){
                  return a.age - b.age;
              })
          })
        }
      }
    }
  </script>

  