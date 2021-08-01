<template>
  <div>
    <h2>First Learn Vue 3</h2>
    <input type="text" placeholder="Filter search" v-model="query"/>
    <br>
    <button name="reset" @click="reset">Reset</button>
    <br>
    <search-results :params="query"/>
  </div>
</template>

<script>
import {ref} from 'vue'
import SearchResults from "@/components/SearchResults";

export default {
  name: 'HelloWorld',
  components: {SearchResults},
  setup() {
    const query = ref('')
    const reset = () => {
      query.value = ''
    }
    return {
      query,
      reset
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
input[type='text'] {
  margin-bottom: 20px;
  padding: 10px;
  border-style: dashed;
  border-color: antiquewhite;
}

input[type='text']:hover, input[type='text']:focus {
  border-color: aquamarine;
  border-style: groove;
}

button[name='reset'] {
  background-color: darkgoldenrod;
  border: 1px coral;
  border-radius: 3px;
  padding: 5px;
  color: #868281;
}

button[name='reset']:hover {
  background-color: aquamarine;
  cursor: pointer;
}
</style>
