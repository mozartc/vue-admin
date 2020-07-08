<template>
<div >
   <svg class="icon" aria-hidden="true" > 

                        <use xlink:href='#icon-fuzhi'></use>

                    </svg>
    <span class="iconfont icon-copy">cc</span>
    <span class="iconfont icon-copy">cc</span>
    <el-button @click="init()">click</el-button>
    <el-button @click="init2()">click2</el-button>
    <p
     class="title"
    :title="name"
     >{{name | ellipsis}}</p>
</div>

</template>



<script>
export default {
  filters: {
    ellipsis (value) {
      if (!value) return ''
      if (value.length > 8) {
        return value.slice(0,8) + '...'
      }
      return value
    }
  },
    data() {
      return {
        name:'中国美国日本新加坡加拿大法国意大利'
      };
    },
    methods: {
      init(){
          const uus=[
              {props:{
                  type:'select',
                  onSuccess:function(res,file){
                      file.url = res.data.filePath
                  }
              }}
          ];
          console.log("第一",uus);
            var s=JSON.stringify(uus, function(key, val) {
            if (typeof val === 'function') {
                return val + '';
            }
            return val;
            });
           console.log("第二",s); 
           var tt = JSON.parse(s,function(k,v){
            if(v.indexOf && v.indexOf('function') > -1){
                console.log("中间",v)
                return eval("(function(){return "+v+" })()")
            }
            return v;
            });
            console.log("第三",tt); 
      },
      init2(){
        const myDate = new Date();
        let cc = '';
        const month = this.fn3(myDate.getMonth()+1,2)
        const date = this.fn3(myDate.getDate()+1,2)
        cc = 'e'+month+date+
        console.log(cc)
      },
      fn3(num, length) {  
          return (Array(length).join('0') + num).slice(-length);  
      }  
    }
  }
</script>