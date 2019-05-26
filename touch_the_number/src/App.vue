<template>
  <div>
    <myheader></myheader>
    <p v-if="msg.length > 0">
      {{msg}}
    </p>
    <p v-else>
      no text
    </p>
    <input type="text" v-model="msg">
    <button @click="clear()">clear</button>
  </div>
    <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
  <!-- </div> -->
</template>

<script>
import myheader from './components/myheader.vue' 
// import HelloWorld from './components/HelloWorld.vue'

// export default {
//   name: 'app',
//   components: {
//     HelloWorld
//   }
// }

export default {
  components:{
    myheader
  },
  data () {
    return {
      msg: 'ここに文字を出す!'
    }
  },
  methods:{
    clear(){
      this.msg = ''
    }
  },
  created () {
    fetch('http://www.geonames.org/postalCodeLookupJSON?postalcode=10504&country=US')
    .then( response => {
      return response.json()
    })
    .then( json => {
      this.msg = json.postalcodes[0].adminName1
    })
    .catch( () => {
    });
  }
}
</script>

<style>
/* #app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
} */
</style>
