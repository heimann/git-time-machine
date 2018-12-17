<template>
  <div class="hello" @click="hideResults">
    <h1>Git Time Machine</h1>
    <input type="text"
           id="repo"
           name="repo"
           minlength="4"
           maxlength="40"
           size="10"
           v-model="search"
           @input="onChange"/>
    <ul 
      class="results"
      v-show="isOpen"
    >
      <li v-for="(result, i) in results" :key="i" class="result">
        {{ result }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    items: {
      type: Array,
      required: false,
      default: () => [],
    },
  },
  data() {
    return {
      search: '',
      results: [],
      isOpen: false,
    };
  },
  methods: {
    onChange() { 
      if (this.search == '') {
        this.isOpen = false
      } else {
        this.isOpen = true;
        this.filterResults();
      }
    },
    filterResults() {
      this.results = this.items.filter(item => item.toLowerCase().indexOf(this.search.toLowerCase()) > -1);
    },
    hideResults() {
      this.isOpen = false;
    }
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}

.hello {
  margin-top: 30vh;
}

#repo {
  width: 550px;
  height: 40px;
  font-size: 1em;
  font-weight: 400;
  border: 1px solid #bababa;
  box-sizing: border-box;
  padding: 0 12px;
  -webkit-box-shadow: 5px 5x 17px 0px rgba(224,224,224,0.76);
  -moz-box-shadow: 5px 5px 17px 0px rgba(224,224,224,0.76);
  box-shadow: 5px 5px 17px 0px rgba(224,224,224,0.76);
}

#repo:hover {
  -webkit-box-shadow: 5px 5px 17px 0px rgba(224,224,224,1);
  -moz-box-shadow: 5px 5px 17px 0px rgba(224,224,224,1);
  box-shadow: 5px 5px 17px 0px rgba(224,224,224,1);
}

#repo:focus {
  outline: none;
  -webkit-box-shadow: 5px 5px 17px 0px rgba(224,224,224,1);
  -moz-box-shadow: 5px 5px 17px 0px rgba(224,224,224,1);
  box-shadow: none;
}
.results {
  box-sizing: border-box;
  width: 550px;
  border: 1px solid #bababa;
  display: block;
  margin: 0 auto;
  padding: 0;
  z-index: 1;
  margin-top: -1px;
  position: relative;
  list-style: none;
}
</style>
