<template>
    <div>
        <div v-if="user==null">
            <button @click="login()">Login</button>
        </div>
        <div v-if="user!=null">
            <p>User: {{this.user.displayName}}</p>
            <button @click="logout()">Logout</button>
        </div>
    </div>
</template>


<style>

</style>

<script>
import firebase from "firebase"

// Initialize Firebase
const firebaseConfig = {
    apiKey: "XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
    authDomain: "xxxxxxxxx.firebaseapp.com",
    databaseURL: "https://xxxxxxxxxx.firebaseio.com",
    projectId: "xxxxxxxxx",
    storageBucket: "xxxxxxxxxx.appspot.com",
    messagingSenderId: "8888888888"
};
firebase.initializeApp(firebaseConfig);


export default {
  name: 'authtest',
  data () {
    return {
        user: null,
    }
  },
  mounted() {
        firebase.auth().onAuthStateChanged(user => {
            console.log("UserChange:", user);
            this.user = user;            
        })
  },
  methods: {
        login() {
            const provider = new firebase.auth.GoogleAuthProvider()
            //firebase.auth().signInWithPopup(provider)
            firebase.auth().signInWithRedirect(provider);
        },
        logout() {
            firebase.auth().signOut()
        }
      
  }

}
</script>
