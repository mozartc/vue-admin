<template>
    <div id="app">
      <form-create :rule="ruleQ" />
      <FormCreate :rule="rule" v-model="fApi" :option="options" ref="refU"/>
      <el-button @click="change">ww</el-button>
    </div>
</template>



<script>

export default {
        data(){
            return {
                fApi:{},
                options:{
                    onSubmit:(formData)=>{
                        console.log("ok")
                    },
                    resetBtn:true,
                    submitBtn:false
                },
                rule:[
                    {type: "select",
                      field: "cate_id",
                      title: "产品分类",
                      value: [],
                      options: [
                          {"value": "104", "label": "生态蔬菜", "disabled": false},
                          {"value": "105", "label": "新鲜水果", "disabled": false},
                      ],
                      props: {
                          multiple: true
                      },
                      validate:[{
                        required:true,message:"不可为空",trigger:'change'
                      }]
                    },
                    {
                    type: "autoComplete",
                    title: "自动完成",
                    field: "auto",
                    value: "xaboy",
                    props: {
                          "fetchSuggestions": function (queryString, cb) {
                          cb([
                            {value: queryString}, {value: queryString + queryString}
                          ]);
                        }
                      }
                    }
                ],
                ruleQ: [],
              optionsQ:[
                {type:'33',"value": "104", "label": "生态蔬菜", "disabled": false},
                {type:'44',"value": "105", "label": "新鲜水果", "disabled": false},
              ],
              addRule:
                {
                              type:"input",
                              title:"",
                              field:"goods_name",
                              value:"",
                              col:{
                                span:8
                              },
                              props: {
                                  "type": "text",
                              }
                          }
              
            }
            
        },
        created() {
          this.init();
        },
        methods:{
          change(){
            console.log(this.$refs.refU)
            this.$refs.refU.$f.validate((valid) =>{
              console.log("cc")
            })
          },
          init(){
            this.ruleQ=[{
                  type:'group',
                  title:'批量添加',
                  field:'group',
                  value:[],
                  props:{
                      rules:[
                          {
                             type: "select",
                              field: "cate_id",
                              title: "",
                              value: '',
                              options: this.optionsQ,
                              props: {
                                  multiple: false
                              },
                              col:{
                                  span:8
                              },
                              on:{
                                change:((value) =>{
                                  console.log("ak48",value)
                                  this.optionsQ.find(item =>{
                                    if(item.value === value){
                                      console.log("type",item.type)
                                      console.log("uuc",this.ruleQ['0'].props.rules)
                                      this.ruleQ['0'].props.rules.push(this.addRule)
                                    }
                                  })
                                }
                                )
                              }

                          },
                          {
                              type: "select",
                              field: "cate_id2",
                              title: "",
                              value: '',
                              options: this.optionsQ,
                              props: {
                                  multiple: false
                              },
                              col:{
                                  span:8
                              }
                          }
                          
                      ]
                  }
              }]
          }
        }
    }
</script>