<template>
  <div id="app">
    <tags v-model="tags" color="danger" />
      {{ tags }}

    <hr>
    <tags v-model="tags2"  color="warning"/>
      {{ tags2 }}

    <hr>
    <tags v-model="tags3" color="success"/>
      {{ tags3 }}

    <hr>
  </div>
</template>

<script>
import tags from "./components/tags"

export default {
  name: 'app',
  components: {
    tags
  },
  data() {
    return {
      tags: "deneme,test,veysel,kars",
      tags2: "deneme,test,veysel,kars,istanbuk,sivas",
      tags3: "deneme,test,veysel,kars,mardin,"
    }
  }


}
</script>

<style>


</style>
