<template>
    <div>
        <div v-if="user==null">
            <div id="firebaseui-auth-container"/>
        </div>
        <div v-if="user!=null">
            <p>Loggin {{user.displayName}}</p>
        </div>
    </div>
</template>

<script>
import firebase from "firebase";
import 'firebase/auth'

const uiConfig = {
  signInSuccessUrl: '/',
  signInOptions: [
    firebase.auth.GoogleAuthProvider.PROVIDER_ID,
  ],
};

// Initialize Firebase
const firebaseConfig = {
    apiKey: "XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
    authDomain: "xxxxxxxx.firebaseapp.com",
    databaseURL: "https://xxxxxxxx.firebaseio.com",
    projectId: "xxxxxxxxxxx",
    storageBucket: "xxxxxxxxxxx.appspot.com",
    messagingSenderId: "888888888888"
};

export default {
    data() {
        return {
            user: null,
        }
    },
    mounted() {
        if (!firebase.apps.length && process.browser) {
        require('firebaseui/dist/firebaseui.css');
        const firebaseui = require('firebaseui');
        firebase.initializeApp(firebaseConfig);

        const ui = firebaseui.auth.AuthUI.getInstance() || new firebaseui.auth.AuthUI(firebase.auth());
        ui.start("#firebaseui-auth-container", uiConfig);

        firebase.auth().onAuthStateChanged(user => {
            console.log("UserChange:", user);
            this.user = user;
            console.log("FB", firebase)
            })
        }
    },
}
</script>