<template>
  <div class="root">
    <div class="search">
      <el-card class="box-card">
        <el-input placeholder="请输入服务商名称" v-model="searchObj.providerName" clearable>
          <el-button @click="goSearch" slot="append" icon="el-icon-search"></el-button>
        </el-input>
      </el-card>
    </div>
    <div class="container">
      <el-table :data="tableData" style="width: 100%">
        <el-table-column
          v-for="(item) in tableHeader"
          :prop="item.propName"
          :label="item.label"
          :key="item.id"
          :width="item.width"
        ></el-table-column>
        <el-table-column fixed="right" label="操作" width="120">
          <template slot-scope="scope">
            <el-button
              @click.native.prevent="onEdit(scope.$index, tableData)"
              type="text"
              size="small"
            >编辑</el-button>
            <el-button
              @click.native.prevent="deleteRow(scope.$index, tableData)"
              type="text"
              size="small"
            >移除</el-button>
          </template>
        </el-table-column>
      </el-table>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      searchObj: {
        providerName: "",
      },
      tableHeader: [
        { label: "供应商", propName: "name" },
        { label: "日期", propName: "date" },
        { label: "地址", propName: "address" },
      ],
      tableData: [
        {
          id: 1,
          name: "王小虎",
          date: "2016-05-02",
          address: "上海市普陀区金沙江路 1518 弄",
          visible: false,
        },
        {
          id: 2,
          date: "2016-05-04",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1517 弄",
          visible: false,
        },
        {
          id: 3,
          date: "2016-05-01",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1519 弄",
          visible: false,
        },
        {
          id: 4,
          date: "2016-05-03",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1516 弄",
          visible: false,
        },
      ],
    };
  },
  methods: {
    goSearch() {
      console.log(this.searchObj.providerName);
    },
    onEdit(i, row) {
      console.log(row[i]);
    },
    deleteRow(i, row) {
      console.log(row[i]);
    },
  },
};
</script>
<style lang="scss">
.search {
  margin-bottom: 10px;
}
</style>