<template>
  <el-row class="fixation">
    <el-col>
      <el-form>
        <el-form-item><p>КОМЕТАРИЙ К ФИКСАЦИИ</p></el-form-item>
        <el-form-item>
          <el-input type="textarea" :rows="5" v-model="textarea" id="textarea"></el-input>
        </el-form-item>
        <el-form-item>
          <!-- <el-input type="submit" id="submit_fixation"></el-input> -->
          <el-button @click.prevent="onsubmit" id="submit_fixation">Отправить</el-button>
        </el-form-item>
      </el-form>
    </el-col>
  </el-row>
</template>
<script>
export default {
  data() {
    return {
      textarea: ''
    }
  },
  methods: {
    onsubmit() {
      var comment = this.textarea;

      console.log('Коментарий:', comment)
    }
  }
}
</script>
<style lang="scss">
.fixation {
  padding: 20px 0 0 40px;

  p { color: rgb(80,80,80); }

  #textarea {
  width: 88%;
  resize: none;
  border: 2px rgb(42,42,42) solid;
  background-color: rgb(31,31,31);
  padding: 12px;
  color: rgb(80,80,80);
  }
  #submit_fixation {
  background-color: rgb(31,31,31);
  border: 2px rgb(80,80,80) solid;
  border-radius: 3px;
  color: rgb(80,80,80);
  float: right;
  margin-right: 12%;
  padding: 10px;
  }
}
</style>
