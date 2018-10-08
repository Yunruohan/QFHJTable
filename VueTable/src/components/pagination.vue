<template>
  <div class="block">
    <div class="tableBorder">
    <el-table     
      :data="tableData"
      style="width:98%;"
      border
      :default-sort = "{prop: 'id', order: 'ascending'}"
      @selection-change="handleSelectionChange"   
      @row-click="handleclick"
      :row-class-name = "tableRowClassName"
      >
      <el-table-column class="type1"
        prop="id"
        label="导入名称"
        show-overflow-tooltip
        highlight-current-row:true
        width="150">
      </el-table-column>
      <el-table-column class="type1"
        prop="createTm"
        label="导入时间"
        sortable
        width="300">
      </el-table-column>
      <el-table-column class="type1"
        prop="state"
        label="导入状态"
        width="300"
      >
      </el-table-column>
      <el-table-column class="type1
      "
        prop="option"
        label="操作"
      >
      <template slot-scope="scope">
        <el-button type="text" size="small"><a href="'http://172.31.3.45:9527/download?uid='+this.tableData.uid" download="template.zip" class="downlinkZip">下载</a></el-button>
      </template>
      </el-table-column>
    </el-table>
    <div align="center">
      <el-pagination
          @size-change="handleSizeChange"
          @current-change="handleCurrentChange"
          :current-page="params.index"
          :page-sizes="[5, 10, 15, 20]"
          :page-size="params.size"
          layout="total, sizes, prev, pager, next, jumper"
          :total="totalCount">
      </el-pagination>
    </div>
    </div>
  </div>
</template>
<script>
import axios from 'axios'
   export default {
    data() {
      return {
        tableData:"",
        params:{index:0,size:5},
        currentPage1: 5,
        currentPage2: 5,
        currentPage3: 5,
        currentPage4: 4,
        totalCount:0
      };
    },
    created(){
      
    },
    mounted(){
      this.data()
    },
    methods: {
     data(){
       axios.get('../../static/json/a.json',{ params: {
        //  size:params.size,
        //  page:params.index
       }
        }).then((res) => {
        console.log(res)
        this.tableData = res.data.data.content
        this.totalCount = res.data.data.content.length
        console.log(this.tableData)
        }).catch(error=>console.log(error))
     },
      handleSizeChange(size) {
        this.params.size = size
        this.data()
      },
      handleCurrentChange(index) {
        this.params.index = index
        this.data()
      }
    }
  }
</script>
<style>
.cell{
  text-align: center;
}
.tableBorder{
  width:100%;
  background: #fff;
}
.title{
  display: block;
  float:left;
  margin-left:20px;
  margin-top:15px;
  text-align: left;
  font-size:25px;
}
.leftMenu{
    width:100px;
    height:100%;
    background: #fff;
    float:left;
}
.block{
  padding:50px;
}
.downBtn{
  float:right;
  margin-right:9%;
  margin-top:20px;
  padding:7px;
  color:#fff;
  font-weight:500;
  background: #00d8ff;
  border-radius: 10%;
}
.upload{
  float:left;
  margin-left:60%;
}
.downlink{
  color:#fff;
}
.downlinkZip{
  color:cornflowerblue;
}
.type1{
  width:100px;
}
.el-table__header-wrapper{
  background-color: #f9f9f9;
}
.el-table{
  margin:10px;
}
.tableBorder{
  padding-top:1px;
  margin-top:10px;
}
</style>
