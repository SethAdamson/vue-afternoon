<template>
  <div id="bots">
    <h3>{{b.botName}}</h3>
    <h4>Attack: {{b.attack}}</h4>
    <h4>Health: {{b.health}}</h4>
    <div class='bot-btn'>
        <button @click="selectBots(b.botName)">Select</button>
        <button @click="deleteBot(i)">Retire</button>
    </div>
  </div>
</template>

<script>
export default {
    props: ['b', 'i', 'selectBots', 'deleteBot'],
}
</script>

<style lang="css" scoped>
#bots {
}

h3 {
  margin: 20px;
  font-size: 24px;
}

h4 {
  margin: 5px;
}

.bot-btn {
  margin: 30px 30px 10px 30px;
  display: flex;
  justify-content: space-between
}
button {
  background: transparent;
  border: none;
  font-size: 18px;
  color: navy;
  font-family: 'Orbitron', sans-serif;
}

</style>
