<template>
  <el-row class="info_right">
    <el-col :span="24">
        <vue-modaltor  :visible="open" @hide="hideModal" :default-width="'20%'" :bg-overlay="'rgba(255,255,255,0.1)'">
          <el-form class="house_form">
            <el-form-item id="margin-form">
              <el-input v-model="form.name" :placeholder="labels.name" id="input-style"></el-input>
            </el-form-item>
            <el-form-item id="margin-form">
              <el-input v-model="form.area" :placeholder="labels.area" id="input-style"></el-input>
            </el-form-item>
            <el-form-item id="margin-form">
              <el-button type="primary" id="button-style" @click="addHouseComplex">{{ labels.submit }}</el-button>
            </el-form-item>
          </el-form>
        </vue-modaltor>


      <el-row class="new_complex">
        <el-col :span="24">
          <el-button @click="open=true" type="primary" icon="el-icon-plus" circle id="btn_new_complex"></el-button>
          <span class="add_complex">Жилой комплекс</span>
        </el-col>
      </el-row>

      <div v-if="total > 0">
        <div v-for="(item, key) in list" :key="key" class="house_complex">
          <a @click="$emit('house-chosen', key, item.title, item.area)">{{ item.title }}<br />({{ item.area }})</a>
        </div>
      </div>

    </el-col>
  </el-row>
</template>

<script>
  export default {
    data() {
      return {
        labels: {
          name: "Название",
          area: "Район",
          submit: "Добавить"
        },
        formVisible: false,
        form: {
          name: "",
          area: ""
        },

        total: 0,
        list: [],
        open: false
      }
    },
    methods: {
      hideModal() {
              this.open = false
          },

      addHouseComplex() {
        if (this.form.name !== '' &&
        this.form.area !== '') {

          let obj = {
            title: this.form.name,
            area: this.form.area,
          };

          this.list.unshift(obj)
          this.total = this.list.length

          this.formVisible = false;
          this.form.name = '';
          this.form.area = '';
        }
      }
    }
  }
</script>

<style lang="scss">
  .info_right {
    margin: 46px 0 0 4px;

    .house_form { padding-top: 20px; }
    .add_complex { color: rgb(97,97,97); }

    .new_complex {
      div {
        border: 1px rgb(16,48,52) solid;
        background-color: rgb(16,48,52);
        padding: 5px 0 2px 6px;
        font-size: 14px;
      }
      #btn_new_complex {
        background-color: rgb(16,48,52);
        padding: 3px;
        font-size: 10px;
        color: #409EFF;
      }
    }

    .house_complex {
        border: 1px rgb(16,48,52) solid;
        background-color: rgb(16,48,52);
        margin-top: 3px;
        height: 36px;
        padding-top: 12px;
        text-align: center;
        color: rgb(97,97,97);
        word-break: break-all;
    }
  }

</style>
