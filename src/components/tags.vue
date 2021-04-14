<template>
  <div class="tag-container">
   <tag
      v-for="(tag , index ) in tags"
      :tag="tag"
      :index="index"
      :tagcolor="color"
      @removeOneTagEvent="tagdelete($event)"
   />
    <input type="text"
           @keyup.enter="addtag"
           @keyup.backspace="removetag">
    <div class="error" v-if="error">Bu karakter daha önceden girişmiş</div>
  </div>

</template>
<script>
import tag from "./tag";
export  default {
  components:{
    tag
  },
  data() {
    return {
      tags: [],
      error: false
    }
  },
  methods: {
    addtag(event) {
      let text = event.target;
      let matchedtag = false;
      if (text.value.length > 0) {
        this.tags.forEach(tag => {
          if (tag.toLowerCase() === text.value.toLowerCase()) {
            matchedtag = true
          }
        })
        if (!matchedtag) {
          this.tags.push(text.value);
          text.value = '';
        } else {
          this.error = true
          setTimeout(() => {
            this.error = false;
          }, 2000)
        }
      }
    },
    removetag(e){
      if(e.target.value.length <= 0){
        this.tags.splice(this.tags.length-1,1);
      }
    },
    tagdelete(index){
      this.tags.splice(index,1);
    }

  },
  props:{
   value:{
     required:false
   },
    color:{
     type:String,
      required: false,
      default:"primary"
    }

  },
  created() {
    if(this.value){
      if (this.value.length>0){
        this.tags = this.value.split(",");
      }
    }
  },
  watch:{
    tags(){
      this.$emit("input",this.tags.join(","));
    }
  }
}
</script>
<style scoped>
.tag-container {
  border: 1px solid rgba(188, 188, 188, 0.87);
  overflow: hidden;
  height: 35px;
  padding: 10px 5px 15px;
}

.error {
  color: red;
  font-size: 12px;
}

input {
  padding: 5px;
}

</style>
