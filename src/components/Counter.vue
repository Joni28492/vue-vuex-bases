<template>
  <h1>Counter - Vuex</h1>
  <h2>Direct access: {{ $store.state.counter.count }} </h2>
  <h2>Computed: {{ countComputed }} </h2>

  <button @click="increment" > +1 </button>
  <button @click="incrementBy(5)" > +5 </button>
  <button @click="randomInt" :disabled="isLoading"> random </button>




  <h1>Map State</h1>
  <h2>Map State: {{ count }} </h2>
  <h2>LastMutation: {{ lastMutation }} </h2>



  <h2>Direct Getter: {{ $store.getters['counter/squareCount'] }} </h2>
</template>

<script>


import { mapState, mapActions } from "vuex";



export default {
  // computed:  mapState(['count'])
  computed: {
    countComputed(){
      return this.$store.state.counter.count
    },
    ...mapState('counter',['count', 'lastMutation', 'isLoading'])
    // ...mapState({
    //   count: state => state.count,
    //   lastMutation: state => state.lastMutation
    // })
  },
  methods: {
    increment(){
      this.$store.commit('counter/increment')
    },
    incrementBy(value){
      this.$store.commit(`counter/incrementBy`, value)
    },
    // ...mapActions('counter',['incrementRandomInt'])
    ...mapActions('counter' ,{
      randomInt: 'incrementRandomInt'
    })
    // incrementRandomInt(){
    //   this.$store.dispatch('incrementRandomInt')
    // }
  }
}
</script>

