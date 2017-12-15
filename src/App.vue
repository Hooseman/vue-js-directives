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
                </div>
        </div>
    </div>
</template>

<script>
    export default {
    }
</script>

<style>

</style>
