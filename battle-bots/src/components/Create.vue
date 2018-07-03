<template>
  <div id="create">
      <form @submit.prevent="addBot(botName, attack, health)" class="form-create">
          <input type="text" v-model="botName" placeholder="Bot Name">
          <input type="number" v-model="attack" placeholder="Attack">
          <input type="number" v-model="health" placeholder="Health">
          <div class="create-btn">
              <button :disabled="!botName || !attack || !health">Create</button>
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

<style lang="css" scoped>
#create {
    margin: 50px auto;
    width: 40vw;
    background: white;
    padding: 2%;
    box-shadow: 0px 2px 5px grey;
    border-radius: 3px;
    font-family: 'Orbitron', sans-serif;
}

.form-create {
    display: flex;
    flex-direction: column;
    align-items: center;
}

input {
    width: 100%;
    margin: 10px;
    height: 30px;
    font-family: 'Orbitron', sans-serif;
}

.create-btn {
    margin: 10px;
    display: flex;
    justify-content: space-around;
    width: 80%;
}

button {
    width: 30%;
    height: 40px;
    border: none;
    border-radius: 5px;
    background: rgb(240, 240, 240);
    box-shadow: 0px 2px 5px grey;
    font-family: 'Orbitron', sans-serif;
}

button:disabled {
    background: rgb(200, 200, 200);
    color: grey;
    box-shadow: none;
}

</style>
