<template>
  <div id="app">
  	<el-col :span="4" class="colleft"><Nav></Nav></el-col>
    <el-col :span="20" class="colright"><Csdx></Csdx></el-col>
  </div>
</template>

<!-- <script src="https://cdn.bootcss.com/bootstrap/3.3.7/js/bootstrap.min.js""></script> -->
<script>
import Csdx from './components/base/Csdx'
import Nav from './components/Nav'
// import Nav from './components/Nav'

export default {
  name: 'app',
  components: {
    Csdx,
    Nav
  }
}

</script>

<style>
/*@import 'https://cdn.bootcss.com/bootstrap/3.3.7/css/bootstrap.min.css';*/
body{
	margin: 0;
}
.colleft{
	position: fixed;
	top:0;
	left:0;
	bottom:0;
	background: #eef1f6;
}
.colright{
	margin-left: 16.66666666%;
}
</style>
