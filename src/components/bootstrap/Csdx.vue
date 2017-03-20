<template>
  <div class="col-sm-10">
    <!-- <h1>{{msg}}</h1> -->
    <form class="form-inline">
      <hr/>
      <p>
        <div class="form-group">
          <h3>
            <b>字段</b>
            <button type="button" class="btn btn-info" @click="addField()">添加字段</button>
          </h3>
        </div>
      </p>
      <div v-for="(field,index) in fields">
        <p>
          <div class="form-group">
            <label>字段名</label>
            <input v-model='field.fieldName' type="" class="form-control" placeholder="">
          </div>
          &nbsp;&nbsp;
          <div class="form-group">
            <label>中文名</label>
            <input v-model='field.fieldCnName' type="" class="form-control" placeholder="">
          </div>
          &nbsp;&nbsp;
          <div class="form-group">
            <label>java类型</label>
            <select v-model="field.fieldType" class="form-control">
              <option v-for="option in fieldTypeOptions" :value="option.value">
                {{option.name}}
              </option>
              <!-- <option value="Integer">Integer</option>
              <option value="Date">Date</option>
              <option value="Double">Double</option>
              <option value="BigDecimal">BigDecimal</option>
              <option value="Float">Float</option>
              <option value="Boolean">Boolean</option> -->
            </select>
          </div>
          &nbsp;&nbsp;
          <button type="button" class="btn btn-default" v-if="" @click="removeField(index)">删除</button>
        </p>
      </div >
      </form>
      <form class="form-horizontal">
        <hr/>
        <div class="form-group">
          <label for="tableName" class="col-sm-1 control-label">表名</label>
          <div class="col-sm-2">
            <input v-model="tableName" id="tableName" class="form-control" type="" name="">
          </div>
        </div>
        <div class="form-group">
          <label for="url" class="col-sm-1 control-label">控制器URL</label>
          <div class="col-sm-2">
            <input v-model="url" id="url" class="form-control">
          </div>
        </div>
        <div class="form-group">
          <label></label>
          <label class="col-sm-1 control-label">主键自增</label>
          <label class="radio-inline">
            <input v-model="isAutoIncrement" name="isAutoIncrement" type="radio" id="isAutoIncrementTrue" value="1">
            <label for="isAutoIncrementTrue">是</label>
          </label>
          <label class="radio-inline">
            <input v-model="isAutoIncrement" name="isAutoIncrement" type="radio" id="isAutoIncrementFalse" value="0">
            <label for="isAutoIncrementFalse">否</label>
          </label> 
        </div>
        <div class="form-group">
          <label></label>
          <label class="col-sm-1 control-label">update使用if判断</label>
          <label class="radio-inline">
            <input v-model="isUpdateUseIf" name="isUpdateUseIf" type="radio" id="isUpdateUseIfTrue" value="1">
            <label for="isUpdateUseIfTrue">是</label>
          </label>
          <label class="radio-inline">
            <input v-model="isUpdateUseIf" name="isUpdateUseIf" type="radio" id="isUpdateUseIfFalse" value="0">
            <label for="isUpdateUseIfFalse">否</label>
          </label> 
        </div>
        <div class="form-group">
          <label></label>
          <label class="col-sm-1 control-label">生成BUI表格</label>
          <label class="radio-inline">
            <input v-model="isAdminTable" name="isAdminTable" type="radio" id="isAdminTableTrue" value="1">
            <label for="isAdminTableTrue">是</label>
          </label>
          <label class="radio-inline">
            <input v-model="isAdminTable" name="isAdminTable" type="radio" id="isAdminTableFalse" value="0">
            <label for="isAdminTableFalse">否</label>
          </label> 
        </div>
        <div class="form-group">
          <label></label>
          <label class="col-sm-1 control-label">表格数据使用DTO</label>
          <label class="radio-inline">
            <input v-model="isUseDto" name="isUseDto" type="radio" id="isUseDtoTrue" value="1">
            <label for="isUseDtoTrue">是</label>
          </label>
          <label class="radio-inline">
            <input v-model="isUseDto" name="isUseDto" type="radio" id="isUseDtoFalse" value="0">
            <label for="isUseDtoFalse">否</label>
          </label> 
        </div>
        <div class="form-group">
          <label></label>
          <label class="col-sm-1 control-label">增加/修改</label>
          <label class="radio-inline">
            <input v-model="isSave" name="isSave" type="radio" id="isSaveTrue" value="1">
            <label for="isSaveTrue">是</label>
          </label>
          <label class="radio-inline">
            <input v-model="isSave" name="isSave" type="radio" id="isSaveFalse" value="0">
            <label for="isSaveFalse">否</label>
          </label>
        </div>
        <div class="form-group">
          <label></label>
          <label class="col-sm-1 control-label">删除</label>
          <label class="radio-inline">
            <input v-model="isDel" name="isDel" type="radio" id="isDelTrue" value="1">
            <label for="isDelTrue">是</label>
          </label>
          <label class="radio-inline">
            <input v-model="isDel" name="isDel" type="radio" id="isDelFalse" value="0">
            <label for="isDelFalse">否</label>
          </label>
        </div>
        <hr/>
        <button @click="download()" type="button" class="btn btn-primary">下载</button>
      </form>
    <!-- {{ fields }} -->
  </div>
</template>

<script>
// var $ = require('jquery')

export default {
  name: 'Csdx',
  data () {
    return {
      msg: '生成csd',
      fields: [
        {fieldName: '', fieldCnName: '', fieldType: 'String'}
      ],
      fieldTypeOptions: [
        {value: 'String', name: 'String'},
        {value: 'Integer', name: 'Integer'},
        {value: 'Date', name: 'Date'},
        {value: 'Double', name: 'Double'},
        {value: 'BigDecimal', name: 'BigDecimal'},
        {value: 'Float', name: 'Float'},
        {value: 'Boolean', name: 'Boolean'}
      ],
      tableName: '',
      url: '',
      isAutoIncrement: 1,
      isUpdateUseIf: 1,
      isAdminTable: 1,
      isUseDto: 1,
      isSave: 1,
      isDel: 1
    }
  },
  methods: {
    addField: function () {
      this.fields.push({fieldName: '', fieldCnName: '', fieldType: 'String'})
    },
    removeField: function (index) {
      console.log(index)
      this.fields.splice(index, 1)
    },
    download: function () {
      console.log(this.fields)
    }
  },
  create: function () {
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
form{margin-left: 50px;}
</style>
