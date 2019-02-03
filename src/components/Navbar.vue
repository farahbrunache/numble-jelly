<template>
  <div class="nav-wrapper">
    <nav class="navbar">
      <div class="container">
        <router-link :to="{name : 'Home'}" class="brand-logo left">NJ</router-link>

        <ul class="right">
          <li>
            <router-link :to="{name : 'Add'}">
              <i class="fas fa-layer-plus"></i>
            </router-link>
          </li>
          <li>
            <router-link :to="{name : 'Cart'}">
              <i class="fas fa-cart-arrow-down"></i>
            </router-link>
          </li>
          <li>
            <router-link :to="{name : 'Wish'}">
              <i class="fas fa-stars"></i>
            </router-link>
          </li>
          <li v-if="!user">
            <router-link :to="{name: 'Signup'}">Signup</router-link>
          </li>
          <li v-if="!user">
            <router-link :to="{name: 'Login'}">Login</router-link>
          </li>
          <li v-if="user">
            <a>{{user.email}}</a>
          </li>
          <li v-if="user">
            <a @click="logout">Logout</a>
          </li>
        </ul>
      </div>
    </nav>
  </div>
</template>

<script>
import firebase from 'firebase'
export default {
  name: 'Navbar',
  data () {
    return {
      user: null
    }
  },
  methods: {
    logout(){
      firebase.auth().signOut().then(()=>{
        this.$router.push({name: 'Home'})
        
      })
    }
  },
  created(){
    //let user = firebase.auth().currentUser
    firebase.auth().onAuthStateChanged((user) => {
      if(user){
        this.user = user
        console.log(user);
      }else {
        this.user = null
      }
    })


  }
}
</script>


<style scoped>
.nav-wrapper {
  background-color: white !important;
}
</style>

