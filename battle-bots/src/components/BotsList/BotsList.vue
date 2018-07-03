<template>
  <div id="bots">
    <h3>{{b.botName}}</h3>
    <h4>{{b.attack}}</h4>
    <h4>{{b.health}}</h4>
    <div>
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

<style lang="scss">

</style>
