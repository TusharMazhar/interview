<script setup>
import axios from 'axios'
import { onBeforeMount,ref,computed } from 'vue';

let userInfo = ref([])
let search = ref('')

const getUser = async ()=>{
  await axios.get('http://52.77.211.222:3000/users')
     .then((user)=>{
       console.log(user.data)
       userInfo.value = user.data
     })
     .catch(()=>{
       
     })

    
}


computed(()=>{

})


onBeforeMount(()=>{
   getUser()
})



</script>

<template>
  <div class="main-div">
      <div  v-for="user in userInfo" :key="user.id" class="card"> 
 
          <div > 
            <img :src="`https://robohash.org/${user.id}?size=300x300`" alt="">
          </div>
          <p>{{user.email}}</p>
          <span>{{user.bio}}</span>
       </div>
      
  </div>

</template>

<style scoped>
.main-div{
  display: flex;
}
.card{
  background-color: rgb(76, 113, 113);
  width: 300px;
  min-height: 400px;
  margin: 5px;
}
</style>
