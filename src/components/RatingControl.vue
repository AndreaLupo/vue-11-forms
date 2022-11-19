<template>
  <ul>
    <li :class="{active: modelValue === 'poor'}"><button type="button" @click="activate('poor')">Poor</button></li>
    <li :class="{active: modelValue === 'average'}"><button type="button" @click="activate('average')">Average</button>Average</li>
    <li :class="{active: modelValue === 'great'}"><button type="button" @click="activate('great')">Great</button>Great</li>
  </ul>
</template>

<script>
export default {
  data() {
    return {
      // init the value with the prop got from extern
      // activeOption: this.modelValue // not good since it's not updated
    };
  },
  // special prop used on custom component so that you can use v-model on it for example in a form
  props: ['modelValue'],
  // special event that vue expects to do the bind
  emits: ['update:modelValue'],
  methods: {
    activate(opt) {
      this.$emit('update:modelValue', opt);
    }
  }

}
</script>

<style scoped>
.active {
  border-color: #a00078;
}
.active button {
  color: #a00078; 
}

ul {
    list-style: none;
    margin: 0.5rem 0;
    padding: 0;
    display: flex;
}

li {
    margin: 0 1rem;
    border: 1px solid #ccc;
    padding: 1rem;
    display: flex;
    justify-content: center;
}

button {
    font: inherit;
    border: none;
    background-color: transparent;
    cursor: pointer;
}

</style>