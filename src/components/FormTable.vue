<template>
  <div id="form-table">
    <el-form ref="form" :model="formData" @validate="validate">
      <el-table :data="formData.tableData" border>
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
    <el-button @click="submit">提交</el-button>
  </div>
</template>

<script>
export default {
  name: 'FormTable',
  data() {
    return {
      err: 'qq',
      formData: {
        tableData: [
          { id: 1, name: 'codervae', age: 19 }
        ]
      },
      rules: {
        id: [
          { required: true, message: '请输入id', trigger: 'blur' }
        ],
        name: [
          { required: true, message: '请输入名称', trigger: 'blur' },
          { min: 3, max: 5, message: '长度在 3 到 5 个字符', trigger: 'blur' }
        ]
      },
      validateIndex: []
    }
  },
  methods: {
    addRow(row) {
      this.formData.tableData.push({})
    },
    removeRow(index) {
      this.formData.tableData.splice(index, 1)
    },
    submit() {
      this.$refs.form.validate((res, obj) => {
        console.log(res, obj)
        // const index = Number(obj.split('.')[1])
        // this.validate.push(index)
      })
    }
  }
}
</script>

<style scoped>
#form-table {
  width: 800px;
  margin: 0 auto;
}
::v-deep.el-form-item {
  margin: 17px 0;
  margin: 0;
}
::v-deep .el-form-item__content .el-form-item__error {
  position: static;
}
</style>
