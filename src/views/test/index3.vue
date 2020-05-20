<template>
    <div id="app">
  <form-create v-model="fApi" :rule="rule" :option="option"></form-create>
    </div>
</template>



<script>

export default {
  data () {
    return {
     //实例对象
     fApi:{},
     //表单生成规则
     rule:[
       {
          type: "upload",
          field: "pic",
          title: "轮播图",
          value: [
              'http://img1.touxiang.cn/uploads/20131030/30-075657_191.jpg',
              'http://img1.touxiang.cn/uploads/20131030/30-075657_191.jpg'
              ],
    props: {
        "type":"select",
        "uploadType":"image",
        "action": "",
        "name":"pic",
        "multiple": true,
        "accept":".jpg",
        "limit": 2,
        "onSuccess":function (res, file) {
            file.url = res.data.filePath;
        }
    },
}
     ]
    };
  }
};
</script>