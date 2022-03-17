<template>
<div class="user-profile">
    <div class="user-profile__user-panel">
        <h1 class="user-profile__username"> @_{{user.name}} </h1>
        <div v-if="user.isAdmin" class="user-profile__admin-badge">
            Admin
        </div>
        <div v-else class="user-profile__admin-badge">
            Non Admin
        </div>
        <div class="user-profile__follower-count">
            <strong>followers : </strong> {{follower}}
            <!-- <br>
          <button v-on:click="followUser">Follow</button> 
            <button @click="followUser">Follow</button>
            <button @click="clearAll">ClearAll</button> -->
        </div>
    </div>
    <div class="user-profile__twitte-wrapper">
    <TwootItem v-for="twitte in user.twittes" :key="twitte.id" :username="user.name" :twoot="twitte" @favourite="toggleFavourite"/>
    </div>
</div>
</template>

<script>
import TwootItem from './TwootItem.vue'
export default {
    name: 'UserProfile',
    components: {
        TwootItem
    },
    data() {
        return {
            follower: 0,
            user: {
                name: 'a_k_goel',
                firstName: 'Akshay',
                lastName: 'Goel',
                email: 'akgoeltech@gmail.com',
                isAdmin: true,
                twittes: [{
                        id: 1,
                        content: "twitter is amazing!!! "
                    },
                    {
                        id: 2,
                        content: "One more twitte : please suscribe "
                    }
                ]
            }
        }
    },
    watch: {
        //used when you want to trigger something if someting happens
        //i.e : when you have new follwer you want to send notification 
        //we can also watch comuted property
        follower(newCount, oldCount) {
            if (oldCount < newCount) {
                console.log(`${this.fullName} gained the follower`)
            } else {
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
        followUser() {
            this.follower++;
        },
        clearAll() {
            this.follower = 0
        },
        toggleFavourite(id){
            console.log(`id is retruned backed to parent from child  #${id}`)
        }
    },
    mounted() {
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
    margin-right: auto;
    padding: 20px;
    background-color: white;
    border-radius: 5px;
    border: 2px solid #94bdee;
    justify-content: center
}

h1 {
    margin: 0;
}

.user-profile__admin-badge {
    background: purple;
    color: white;
    margin-right: auto;
    border-radius: 5px;
    font-weight: bold;

}
</style>
