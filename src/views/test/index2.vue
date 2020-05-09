<template>
<!-- <el-cascader :props="props"
filterable>
</el-cascader> -->

<el-select v-model="value" placeholder="请选择" @change="handelChange">
    <el-option
      v-for="item in options"
      :key="item.value"
      :label="item.label"
      :value="item.value"
      >
    </el-option>
  </el-select>
</template>



<script>
let id = 0;

  export default {
    data() {
      return {
          options: [{
          value: '选项1',
          label: '黄金糕'
        }, {
          value: '选项2',
          label: '双皮奶'
        }, {
          value: '选项3',
          label: '蚵仔煎'
        }, {
          value: '选项4',
          label: '龙须面'
        }, {
          value: '选项5',
          label: '北京烤鸭'
        }],
        value: ''
      };
    },
    methods:{
        handelChange(value){
            console.log(this.options)
            console.log(value)
            let obj = {};
            obj = this.options.find((item)=>{//这里的userList就是上面遍历的数据源
                return item.value === value;//筛选出匹配数据
            });
            console.log(obj);
            console.log(obj.value);
            console.log(obj.label);
        }
    }
  };
</script>