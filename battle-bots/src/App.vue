<template>
  <div id="app">
    <header>
      <button @click="changeTrue">Create</button>
      <h1>Battle-Bots</h1>
      <button @click="changeFalse">Collection</button>
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

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

header {
  display: flex;
  justify-content: space-around
}

h1, h2 {
  font-weight: normal;
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
</style>
