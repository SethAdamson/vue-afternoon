<template>
  <div id="create">
      <form @submit.prevent="addBot(botName, attack, health)">
          <input type="text" v-model="botName" placeholder="Bot Name">
          <input type="number" v-model="attack" placeholder="Attack">
          <input type="number" v-model="health" placeholder="Health">
          <div>
              <button>Create</button>
              <button type="button" >Cancel</button>
          </div>
      </form>
  </div>
</template>

<script>
export default {
    props: ['addBot'],
    data (){
        return {
            botName: '',
            attack: undefined,
            health: undefined,
        }
    },
    methods: {
        cancelNew(){
            this.botName = '';
            this.attack = undefined;
            this.health = undefined;
        }
    },

}
</script>

<style lang="scss">

</style>
