<template>
    <div class="about">
        <h2>{{msg}}</h2>
        <form @submit.prevent="updateInfo">
        <ul>
        <li v-for="(data, index) in infos" :key="index"> 
            {{data.info}}

            <i class="fa fa-edit" @click="editInfo(index)"></i>
        </li>
        </ul>
        <p>{{info}}</p>
        
        <p>Add what you know about me:
        <input type="text" v-model="info" placeholder="What can you say about me">
        </p>
        </form>
    </div>
</template>

<script>
export default {
    name: 'About',
    data(){
        return{
            msg: "Welcome to my About Page",
            info: "",
            infos:[
                {info: "I am a front end developer passionate about creating a friendly user experience making every click comfortable"},

            ]
        }
    }, 
    methods: { updateInfo(){
        {
            this.infos.push({info:this.info}),
            this.info= ""
        }
        },
        removeInfo(id){
            this.infos.splice(id,1);
        }
    }
}
</script>

<style scoped>
input{
    width:calc(100% - 40px);
    padding: 10px 0px;
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
i{
    float: right;
    cursor: pointer;
    margin-right: 5px;
}

</style>

