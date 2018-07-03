<template>
  <div id="app">
    <header>
      <button @click="changeTrue" class="head-btn">Create</button>
      <h1>Battle-Bots</h1>
      <button @click="changeFalse" class="head-btn">Collection</button>
    </header>
    <section v-if="viewToggle">
      <create :addBot='addBot'/>
    </section>
    <section v-else>
      <collection :bots='bots'/>
    </section>
  </div>
</template>

<script>
import Create from './components/Create';
import Collection from'./components/Collection';
export default {
  name: 'Battle-Bots',
  data () {
    return {
      viewToggle: true,
      bots: [
        {
          botName: 'Frank',
          attack: 30,
          health: 20,
        },
        {
          botName: 'Harry',
          attack: 40,
          health: 10,
        },
        {
          botName: 'Pearl',
          attack: 10,
          health: 40,
        },
      ]
    }
  },
  methods: {
    changeTrue(){
      this.viewToggle = true;
    },
    changeFalse(){
      this.viewToggle = false;
    },
    addBot(name, atk, hp){
      this.bots.push({botName:name, attack:atk, health:hp});
      this.changeFalse();
    }
  },
  components: {
    Create: Create,
    Collection: Collection,
  },
}
</script>

<style lang="css" >
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  height: 100vh;
  width: 100vw;
  font-family: 'Orbitron', sans-serif;
  background: #5CDB95;
}

header {
  display: flex;
  justify-content: space-around;
  align-items: center;
  height: 80px;
  background: #05386B;
  color: white;
}

.head-btn {
  background: transparent;
  border: none;
  color: white;
  cursor: pointer;
  font-family: 'Orbitron', sans-serif;
}

h1, h2 {
  font-weight: normal;
  font-size: 30px;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}

button {
  cursor: pointer;
}

button:disabled {
  cursor: not-allowed;
}
</style>
