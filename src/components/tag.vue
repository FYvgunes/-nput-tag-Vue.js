<template>
  <div class="tag" :class="selectedcolor">
    <span class="tag-content">{{ tag }}</span>
    <span class="tag-close" @click="$emit('removeOneTagEvent',index)">x</span>
  </div>
</template>
<script>
export default {
  props: ["tag", "index", "tagcolor"],
  data() {
    return {
      selectedcolor: null
    }
  },
  created() {
    this.selectedcolor = this.tagcolor;
  }
}
</script>
<style scoped>
.primary {
  background-color: #0A5ED7;
  color: #fff;

}

.success {
  background-color: #167347;
  color: #fff;
}

.danger {
  background-color: #BB2D3B;
  color: #fff;
}

.warning {
  background-color: #FFCA2C;
  color: #fff;
}

.info {
  background-color: #0A5ED7;
  color: #fff;
}


.tag {
  display: inline;
  padding: 5px;
  border-radius: 5px;
  line-height: 35px;
  margin-right: 5px;
}
</style>
