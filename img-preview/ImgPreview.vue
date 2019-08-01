<template>
  <div>
    <div @click="seePic()">
      <img v-if="src" :src="src" width="55px" height="55px">
    </div>
    <el-dialog
      class="picture"
      :visible.sync="picture"
      :append-to-body="true"
      :width="width"
    >
      <div @click="close()">
        <img 
          @load="onLoad"
          :src="src"
        >
      </div>
    </el-dialog>
  </div>
</template>

<script>
export default {
  name: 'img-preview',
  data() {
    return {
      picture: false,
      width: ''
    };
  },
  props: {
    src: String
  },
  methods: {
    seePic() {
      this.picture = true;
    },
    close(e) {
      this.picture = false;
    },
    onLoad(e){
      const img = e.target;
      let width = 0;
      if (img.fileSize > 0 || (img.width > 1 && img.height > 1)) {
        width = img.width + 40;
      }
      this.width = width + 'px';
    }
  }
};
</script>
