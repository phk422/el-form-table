<template>
  <div id="form-table">
    <el-form :model="formData">
      <el-table :data="formData.tableData">
        <el-table-column label="id" prop="id">
          <template #default="{row, $index}">
            <el-form-item :prop="'tableData.' + $index + '.id'" :rules="rules.id">
              <el-input v-model="row.id" placeholder="" />
            </el-form-item>
          </template>
        </el-table-column>
        <el-table-column label="name" prop="name">
          <template #default="{row,$index}">
            <el-form-item :prop="'tableData.' + $index + '.name'" :rules="rules.name">
              <el-input v-model="row.name" placeholder="" />
            </el-form-item>
          </template>
        </el-table-column>
        <el-table-column label="操作" prop="name">
          <template #default="{row, $index}">
            <el-button type="primary" @click="addRow(row)">添加</el-button>
            <el-button type="danger" @click="removeRow($index)">删除</el-button>
          </template>
        </el-table-column>
      </el-table>
    </el-form>
  </div>
</template>

<script>
export default {
  name: 'FormTable',
  data() {
    return {
      formData: {
        tableData: [
          { id: 1, name: 'codervae', age: 19 }
        ]
      },
      rules: {
        id: [
          { required: true, message: '请输入id', trigger: 'change' }
        ],
        name: [
          { required: true, message: '请输入名称', trigger: 'blur' },
          { min: 3, max: 5, message: '长度在 3 到 5 个字符', trigger: 'blur' }
        ]
      }
    }
  },
  methods: {
    addRow(row) {
      this.formData.tableData.push({})
    },
    removeRow(index) {
      this.formData.tableData.splice(index, 1)
    }
  }

}
</script>

<style>
#form-table {
  width: 800px;
}
</style>
