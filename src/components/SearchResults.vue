<template>
  <div class="root">
    <p> Showing {{ filteredTitles.length }} results for "{{ params }}"</p>
    <ul>
      <li v-for="title in filteredTitles" :key="title.Page">
        {{ title.Name }}
      </li>
    </ul>
  </div>
</template>

<script>
import {computed, onMounted} from "vue";
import titles from '@/post-data.json'

export default {
  name: "SearchResults",
  props: {
    params: String
  },
  mounted() {
    console.log('mounted')
    console.log(this.$el)
  },
  updated() {
    console.log('updated')
  },
  unmounted() {
    console.log('unmounted')
  },
  setup(props) {
    const filteredTitles = computed(() => {
      return titles.filter(s => s.Name.toLocaleLowerCase().includes(props.params.toLocaleLowerCase()))
    })
    onMounted(() => {
      console.log(props.params)
    })
    return {
      filteredTitles
    }
  }
}
</script>

<style scoped>
.root {
  width: 400px;
  margin: 0 auto;
}

.root p {
  text-align: right;
  font-size: 0.7em;
  margin: 0;
}

ul {
  list-style: none;
  width: 100px 0;
  padding: 0;
  background-color: #fafafa;
  border-radius: 5px;
  border: 1px solid #dddddd;
}

li {
  text-align: left;
  padding: 20px;
  border-bottom: 1px solid #dddddd;
}

li:nth-last-of-type(1) {
  border-bottom: navajowhite;
}
</style>
