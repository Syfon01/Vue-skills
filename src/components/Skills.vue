<template>
  <div class="hello">
    <h1>{{msg}}</h1>

    <form @submit.prevent="addSkill">
      <input type="text" placeholder="Enter your Skill" v-model="skill" v-validate="'min:5'" name="skill">
      {{skill}}
      <transition name="alert-in" enter-active-class="animated flipInX" leave-active-class="animated flipOutX">
      <p class="alert" v-if="errors.has('skill')">{{errors.first('skill')}}</p>      
      </transition>
    </form>
    <div class="holder">
      <ul>
        <transition-group name="list" enter-active-class="animated bounceInUp" leave-active-class="animated bounceOutDown">
          <li v-for="(data, index) in skills" :key="index">
          {{data.skill}}

          <i class="fa fa-minus-circle" @click="remove(index)"></i>
          </li>
        </transition-group>
        
      </ul>
      <p>These are the skills you posses</p>
    </div>
  
  </div>
</template>

<script>
export default {
  name: 'Skills',
  data (){
    return{
    msg:'Welcome to my Skill app',
    skill:'',
    skills:[
      {skill: 'Vue js'},
      {skill: 'Figma Design'},
    ]
    }
  },
    methods:{
      addSkill(){
        this.$validator.validateAll().then((result) =>{
          if (result){
            this.skills.push({skill:this.skill}),
            this.skill=""
          }else{
            return 'this is not valid'
          }
        })        
      },
      remove(id){
        this.skills.splice(id,1)
      }
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.holder{
  background:#fff;
}
ul{
  list-style: none;
  margin: 0;
  padding: 0;
}
li{
  border-left:5px solid blueviolet; 
  background-color: #e0edf4;
  margin-bottom: 2px;
  color: #3e5252;
  padding: 10px 5px;
  font-weight:400;
  font-size: 18px;
}
p{
  background: #fff;
  color:#000;
  padding: 10px 0px;
}
input{
  width:calc(100% - 40px);
  border: 0;
  padding: 20px;
  background-color: #323333;
  color: #687f7f;
  font-size: 18px;
}
.alert{
  color: red;
  padding: 10px;
}
i{
  float:right;
  cursor: pointer;
}
</style>
