<template>
  <div id="collection">
      <div class="fight">
          <h2>Bot #1: {{bot1 ? bot1 : 'Select a bot below'}}</h2>
          <h2>Bot #2: {{bot2 ? bot2 : 'Select a bot below'}}</h2>
          <div>
              <button :disabled='!bot1 || !bot2' @click="battle">Battle</button>
              <button @click="clearBots">Clear</button>
          </div>
      </div>
      <hr>
      <div class="list-parent">
        <div class="bot-list" v-for="(b, i) in bots" :key="i">
            <bots-list :b='b' :i='i' :selectBots='selectBots' :deleteBot='deleteBot'/>
        </div>
      </div>
  </div>
</template>

<script>
import BotsList from './BotsList/BotsList';
export default {
    props: ['bots'],
    data(){
        return{
            bot1: '',
            bot2: '',
        }
    },
    methods: {
        selectBots(b){
            if(!this.bot1){
                this.bot1 = b;
            } else if (this.bot1 && !this.bot2){
                this.bot2 = b;
            }
            return;
        },
        clearBots(){
            this.bot1 = '';
            this.bot2 = '';
        },
        deleteBot(i){
            this.bots.splice(i, 1);
        },
        battle(){
            let rando = Math.floor(Math.random() * 100);
            if(rando%2 === 0){
                alert(`${this.bot1} wins!`);
            } else {
                alert(`${this.bot2} wins!`);
            }
        }
    },
    components: {
        BotsList: BotsList,
    }



}
</script>

<style lang="css" scoped>
.fight {
    padding: 25px 0 15px 0;
}

h2{
    font-size: 20px;
}

button {
    margin: 20px 10px 0 10px;
    width: 10%;
    height: 30px;
    background: white;
    border: none;
    box-shadow: 0px 2px 5px grey;
    border-radius: 2px;
    font-family: 'Orbitron', sans-serif;
}

button:disabled {
    background: rgba(0, 0, 0, 0.2);
    color: rgb(90, 90, 90);
    box-shadow: none;
}

.list-parent {
    display: flex;
    flex-wrap: wrap;
    align-items: center;
    justify-content: center;
    max-width: 100vw;
    padding: 30px 10%;
    background: #5CDB95;
}

.bot-list {
    width: 28vw;
    margin: 20px;
    background: white;
    padding: 10px;
    box-shadow: 0px 2px 5px grey;
    border-radius: 2px;
}

</style>
