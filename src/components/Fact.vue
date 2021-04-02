<template>
  <div class="container mx-auto">
    <div
      class="sm:w-1/2 h-80 mx-auto p-4 sm:p-16 shadow-lg my-8 bg-white rounded-md"
    >
      <p class="text-black-800 text-lg">
        {{ this.facts.length ? this.facts[selected].fact : "Loading ..." }}
      </p>
    </div>
  </div>
  <div class="text-center">
    <Button title="Prev" trackName="prev" @prev="handleChange('prev')" />
    <Button title="Next" trackName="next" @next="handleChange('next')" />
  </div>
</template>

<script>
import axios from "axios";
import Button from "./Button.vue";
export default {
  data() {
    return {
      selected: 0,
      facts: [],
    };
  },
  components: {
    Button,
  },
  mounted() {
    axios
      .get("https://dog-facts-api.herokuapp.com/api/v1/resources/dogs/all")
      .then((response) => (this.facts = response.data))
      .catch(function (error) {
        console.log(error);
      });
    setInterval(() => {
      if (this.selected == this.facts.length - 1) {
        this.selected = 0;
      } else {
        this.selected++;
      }
    }, 10000);
  },
  methods: {
    handleChange(direction) {
      if (direction == "prev") {
        if (this.selected == 0) this.selected = this.facts.length - 1;
        else this.selected--;
      } else if (direction == "next") {
        if (this.selected == this.facts.length - 1) {
          this.selected = 0;
        } else {
          this.selected++;
        }
      }
    },
  },
};
</script>