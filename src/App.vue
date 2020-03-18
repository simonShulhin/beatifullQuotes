<template>
  <div class="container">
    <div class="row">
      <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-5 col-md-offset-3">
        <h1>Built-in Directives</h1>
        <p v-text="'Some text'"></p>
        <p v-html="'<strong>Some text</strong>'"></p>
      </div>
    </div>
    <hr />
    <div class="row">
      <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-5 col-md-offset-3">
        <h1>Custom Directives</h1>
        <p v-highlight:backgroundColor.delayed="'red'">Color this</p>
        <p
          v-local-highlight:backgroundColor.delayed.blink="{
            mainColor: 'green',
            secondColor: 'red',
            delay: 200,
          }"
        >
          Color this
        </p>
      </div>
    </div>
    <hr />
  </div>
</template>

<script>
export default {
  name: 'App',
  data: () => ({
    highlighting: {
      mainColor: 'green',
      secondColor: 'red',
      delay: '1000',
    },
  }),
  directives: {
    'local-highlight': {
      bind(el, binding) {
        let delay = 0;
        if (binding.modifiers['delayed']) {
          delay = 3000;
        }
        if (binding.modifiers['blink']) {
          let mainColor = binding.value.mainColor;
          let secondColor = binding.value.secondColor;
          let currentColor = mainColor;
          setTimeout(() => {
            setInterval(() => {
              currentColor == secondColor
                ? (currentColor = mainColor)
                : (currentColor = secondColor);
              binding.arg === 'backgroundColor'
                ? (el.style.backgroundColor = currentColor)
                : (el.style.color = currentColor);
            }, binding.value.delay);
          }, delay);
        } else {
          setTimeout(() => {
            if (binding.arg === 'backgroundColor') {
              el.style.backgroundColor = binding.value.mainColor;
            } else {
              el.style.color = binding.value.mainColor;
            }
          }, delay);
        }
      },
    },
  },
};
</script>

<style></style>
