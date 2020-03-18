<template>
  <div class="quote">
    <form>
      <div class="form-group">
        <label for="">Quote</label>
        <textarea class="form-control" rows="3" v-model="value" required />
        <p>Value of textarea: {{ value }}</p>
      </div>

      <button type="submit" class="btn btn-primary" @click.prevent="createNew">
        Add Quote
      </button>
    </form>
  </div>
</template>

<script>
export default {
  data: () => ({
    value: '',
  }),
  methods: {
    createNew() {
      if (this.value !== '') {
        this.$emit('quoteAdded', this.value);
        this.value = '';
      }
    },
  },
};
</script>

<style scoped>
form {
  margin-bottom: 20px;
  margin-left: 25%;
}

textarea {
  width: 50%;
}
</style>
