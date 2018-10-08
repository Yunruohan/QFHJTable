<template>
    <el-table
      :data="tableData"
      style="width: 30%;margin:0 auto;border:1px solid #ddd;">
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
              this.tableData = res.data;
          })
        }
      }
    }
  </script>

  