<template>
  <button
    class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-5 mr-5 rounded"
    @click="$emit(trackName)"
  >
    {{ title }}
  </button>
</template>

<script>
export default {
  props: ["title", "trackName"],
};
</script>