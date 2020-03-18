<template>
  <div id="counter">
    <h2>Quotes Added</h2>
    <div class="progress">
      <div
        class="progress-bar"
        role="progressbar"
        aria-valuenow="60"
        aria-valuemin="0"
        aria-valuemax="100"
        :style="{width: (quoteCount / maxQuotes) * 100 + '%'}"
      >
        {{ quoteCount }} / {{ maxQuotes }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ['quoteCount', 'maxQuotes'],
};
</script>

<style scoped></style>
