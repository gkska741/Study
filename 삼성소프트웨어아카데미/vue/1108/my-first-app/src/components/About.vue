<template>
  <div id="app">
    <h1>About</h1>
    <h2>{{ myMessage }}</h2>
    <h3>{{ parentData}}</h3>

    <input
     type="text"
     @keyup.enter="childInputChange"
     v-model="childInputData"     
    >
    
  </div>
</template>

<script>
export default {
  name: 'About',
  props: {
    myMessage: String,
    parentData: String,
  },
  methods: {
    childInputChange: function() {
      this.$emit('child-input-change', this.childInputData)
    }
  }
}
</script>

<style>

</style>