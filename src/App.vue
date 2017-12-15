<template>
  <div class="container">
    <div class="row">
      <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
        <h1>Built in Directives</h1>
        <p v-text="'This displays using the v-text'"></p>
        <p v-html="'<strong>this is strong text using v-html</strong>'"></p>
      </div>
    </div>
    <div class="row">
      <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
        <h1>Custom Directives</h1>
        <p>there are 5 hook directives used</p>
        <p>1# bind(el,binding,vnode)</p>
        <p>2# inserted(el,binding,vnode)</p>
        <p>3# update(el,binding,vnode,oldVnode)</p>
        <p>4# componentUpdate(el,binding,vnode,oldVnode)</p>
        <p>5# unbind(el,binding,vnode)</p>
        <!-- used the hook bind to do this -->
        <p v-highlight:background.delayed="'red'">Give me a color</p>
        <p v-local-highlight:background.delayed.blink="{mainColor: 'red', secondColor: 'green', delay: 500}">Give me a local color</p>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    directives: {
      'local-highlight': {
        bind(el, binding, vnode) {
          var delay = 0;
          if (binding.modifiers['delayed']) {
            delay = 3000;
          }
          if (binding.modifiers['blink']) {
            let mainColor = binding.value.mainColor;
            let secondColor = binding.value.secondColor;
            let currentColor = mainColor;
              setTimeout(() => {
                setInterval(() => {
                  currentColor == secondColor ? currentColor = mainColor : currentColor = secondColor;
                   if (binding.arg == 'background') {
                el.style.backgroundColor = currentColor;
              } else {
                el.style.color = currentColor;
              }
                },binding.value.delay);
            }, delay);
          } else {
            setTimeout(() => {
              if (binding.arg == 'background') {
                el.style.backgroundColor = binding.value.mainColor;
              } else {
                el.style.color = binding.value.mainColor;
              }
            }, delay);
          }
        }
      }
    }
  }

</script>

<style>


</style>
