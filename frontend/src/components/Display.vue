<template>
  <el-row class="display_form">
    <el-col>
      <el-form>
        <el-form-item>
          <el-date-picker v-model="value1"
      type="datetime"
      placeholder="Выберите дату и время"></el-date-picker>
        </el-form-item>
        <el-form-item><p>КОМЕНТАРИЙ К ПОКАЗУ</p></el-form-item>
        <el-form-item>
          <el-input type="textarea" :rows="5" v-model="textarea" id="textarea"></el-input>
        </el-form-item>
        <el-form-item>
          <!-- <el-input type="submit" id="submit_display"></el-input> -->
          <el-button @click.prevent="onsubmit" id="submit_display">Отправить</el-button>
        </el-form-item>
      </el-form>
    </el-col>
  </el-row>
</template>
<script>
// import axios from 'axios'

export default {
  data() {
    return {
      value1: '',
      textarea: ''
    }
  },
  methods: {
    onsubmit() {
      var datatime = this.value1;
      var comment = this.textarea;

      console.log('Дата и время:', datatime)
      console.log('Коментарий:', comment)
    }
    // submitDisplay() {
    //   console.log('data', this.value1)
    //   console.log('comment', this.textarea)
    //   axios.post('http://localhost:8081', {
    //      'datatime': this.value1,
    //     'comment': this.textarea
    //            }).then(response => {
    //              console.log(response)
    //             }).catch(error => {
    //             console.log(error)
    //                })
    // }
  }
}
</script>
<style lang="scss">
.display_form {
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
  #submit_display {
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
