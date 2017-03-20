<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <button @click="dod">java后台异步请求</button>
    <div @click='chgt2' id='t2'>{{msg2}}</div> 
  </div>
</template>

<script>
var $ = require('jquery')

export default {
  name: 'hello',
  data () {
    return {
      msg: 'Vue 连接测试'
    }
  },
  methods: {
    dod: function () {
      $.ajax({
        url: '/admin/sa/orderHeaderByAll/json_test',
        type: 'POST',
        dataType: 'json', // here
        success: function (data) {
          console.log(data)
        },
        error: function (msg) {
          console.log(msg)
        }
      })
    }
  },
  create: function () {
    console.log('create')
    $.ajax({
      url: 'http://localhost/json.php',
      type: 'GET',
      dataType: 'JSONP', // here
      success: function (data) {
        console.log(data)
      },
      error: function (msg) {
        console.log(msg)
      }
    })
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
button {
  color: red
}
</style>
