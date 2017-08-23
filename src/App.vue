<template>
  <div id="app">
    <img src="./assets/logo.png">
    <hello></hello>
    <ul>
      <li v-for="flavor in flavors">{{flavor.name}}</li>
    </ul>
  </div>
</template>

<script>
import Hello from './components/Hello'
import Firebase from 'firebase'

let config = {
  apiKey: 'AIzaSyCJDGWXMLRlaTTbV_282w3JGTwivyIdSQE',
  authDomain: 'lacroix-rankings.firebaseapp.com',
  databaseURL: 'https://lacroix-rankings.firebaseio.com',
  projectId: 'lacroix-rankings',
  storageBucket: 'lacroix-rankings.appspot.com',
  messagingSenderId: '675001064580'
}

let app = Firebase.initializeApp(config)
let db = app.database()
let flavorsRef = db.ref('flavors')
console.log(flavorsRef)

export default {
  name: 'app',
  components: {
    Hello
  },
  firebase: {
    flavors: flavorsRef
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
