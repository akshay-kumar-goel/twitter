<template>
  <div class="user-profile">
   <div class="user-profile__user-panel">
    <h1 class="user-profile__username"> @{{user.name}} </h1>
    <div class="user-profile__follower-count">
    <strong>followers : </strong> {{follower}}
    <br>
    <!-- <button v-on:click="followUser">Follow</button> -->
    <button @click="followUser">Follow</button>
    <button @click="clearAll">ClearAll</button>
    </div>
  </div>

  </div>
</template>

<script>

export default{
    name : 'UserProfile',
    data() {
        return {
            follower: 0,
            user: {
                name: 'AKG',
                firstName: 'Akshay',
                lastName: 'Goel',
                email: 'akgoeltech@gmail.com',
                isAdmin: true
            }
        }
    },
    watch:{
  //used when you want to trigger something if someting happens
  //i.e : when you have new follwer you want to send notification 
   //we can also watch comuted property
   follower(newCount, oldCount){
     if(oldCount < newCount){
       console.log(`${this.fullName} gained the follower`)
     }else{
       console.log(`${this.fullName} lost the follower`)
     }

   }

    },
    computed: {
        fullName() {
            return `${this.user.firstName} ${this.user.lastName}`;
        }
    },
    methods: {
        followUser(){
          this.follower++;
        },
        clearAll(){
          this.follower = 0
        }
    },
    mounted(){
      this.followUser()
    }
}
</script>

<style>

.user-profile {
display: grid;
grid-template-columns: 1fr 3fr;
width: 100;
padding: 50px 5%;
}

.user-profile__user-panel {

display: flex;
flex-direction: column;
margin-right: 50px;
padding: 20px;
background-color: white;
border-radius: 5px;
border: 1px solid #DFE3E8
}
h1{
margin: 0;
}

</style>