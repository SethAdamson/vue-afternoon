<template>
  <div id="collection">
      <div class="fight">
          <h2>Bot #1: {{bot1}}</h2>
          <h2>Bot #2: {{bot2}}</h2>
          <div>
              <button :disabled='!bot1 || !bot2' @click="battle">Battle</button>
              <button @click="clearBots">Clear</button>
          </div>
      </div>
      <hr>
      <div class="bot-list" v-for="(b, i) in bots" :key="i">
          <bots-list :b='b' :i='i' :selectBots='selectBots' :deleteBot='deleteBot'/>
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

<style lang="scss">

</style>
