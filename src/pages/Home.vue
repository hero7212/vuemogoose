<template>
  <div class="home">
    <el-row>
      <el-button type="success" @click="showDialog">新增</el-button>
    </el-row>
    <el-table
      ref="multipleTable"
      :data="list"
      tooltip-effect="dark"
      style="width: 100%">
      <el-table-column
        type="selection"
        width="55">
      </el-table-column>
      <el-table-column
        prop="_id"
        label="ID">
      </el-table-column>
      <el-table-column
        prop="name"
        label="姓名">
      </el-table-column>
      <el-table-column
        prop="age"
        label="年龄">
      </el-table-column>
    </el-table>

    <el-dialog :title="dialogTitle" :visible.sync="dialogFormVisible" @close="closeDialog">
      <el-form :model="form">
        <el-form-item label="姓名">
          <el-input v-model="form.name"></el-input>
        </el-form-item>
        <el-form-item label="年龄">
          <el-input v-model="form.age"></el-input>
        </el-form-item>
      </el-form>
      <div slot="footer" class="dialog-footer">
        <el-button type="primary" @click="doSubmit">确 定</el-button>
      </div>
    </el-dialog>

  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'Home',
  data () {
    return {
      list: [],
      dialogTitle: '新增',
      form: {
        name: '',
        age: ''
      },
      dialogFormVisible: false
    }
  },
  methods: {
    doSubmit() {
      if(this.dialogTitle == '新增') {

      }
    },

    showDialog() {
      this.dialogFormVisible = true
    },

    closeDialog() {
      this.dialogFormVisible = false
    },

    async getListAsync() {
      const {data} = await axios.get('api/getList')
      this.list = data;
    },

    async doAdd() {
      const {data} = await axios.post()
    }
  },
  created() {
    this.getListAsync()
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
