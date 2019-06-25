<template>
  <el-row class="clientdeal">
    <el-col>
      <el-col class="head_clientdeal">
        <span>СДЕЛКА ПО ЖК {{ complex }}</span>
        <span class="dash">—</span>
        <span>{{ area }}</span>
        <span class="dash">—</span>
        <span>2.5%</span>
      </el-col>
      <el-col class="form_clientdeal">
        <el-form class="form-pad">
          <el-form-item id="pad"><span>Квартира:</span></el-form-item>
          <el-form-item id="pad"><span>Тип договора:</span></el-form-item>
          <el-form-item id="pad"><span>Номер договора:</span></el-form-item>
          <el-form-item id="pad"><span>Дата договора:</span></el-form-item>
          <el-form-item id="pad"><span>Стоимость покупки:</span></el-form-item>
          <el-form-item id="pad"><span>Комиссия агента:</span></el-form-item>
          <el-form-item label="Файлы ДДУ:" id="pad">
            <el-upload action="https://jsonplaceholder.typicode.com/posts/" :on-preview="handlePreview" :on-remove="handleRemove" :before-remove="beforeRemove" multiple :limit="3" :on-exceed="handleExceed" :file-list="fileList" required>
              <el-button  id="upload_style">загрузить</el-button>
              <div slot="tip" class="el-upload__tip" ></div>
            </el-upload>
          </el-form-item>
          <el-form-item label="Файлы оплаты:" id="pad">
            <el-upload action="https://jsonplaceholder.typicode.com/posts/" :on-preview="handlePreview" :on-remove="handleRemove" :before-remove="beforeRemove" multiple :limit="3" :on-exceed="handleExceed" :file-list="fileList">
              <el-button id="upload_style">загрузить</el-button>
              <div slot="tip" class="el-upload__tip"></div>
            </el-upload>
          </el-form-item>
          <el-form-item label="Прочие файлы:" id="pad" >
            <el-upload action="https://jsonplaceholder.typicode.com/posts/" :on-preview="handlePreview" :on-remove="handleRemove" :before-remove="beforeRemove" multiple :limit="3" :on-exceed="handleExceed" :file-list="fileList">
              <el-button id="upload_style">загрузить</el-button>
              <div slot="tip" class="el-upload__tip"></div>
            </el-upload>
          </el-form-item>
          <el-form-item><p>КОМЕТАРИЙ К СДЕЛКЕ</p></el-form-item>
          <el-form-item>
            <el-input type="textarea" :rows="5" v-model="textarea" id="textarea"></el-input>
          </el-form-item>
          <el-form-item>
            <el-input type="submit" id="submit_clientdeal"></el-input>
          </el-form-item>
        </el-form>
      </el-col>
    </el-col>
  </el-row>
</template>
<script>
export default {
  props: {
    complex: String,
    area: String
  },
  data() {
    return {
      fileList: [],
      textarea: ''
    }
  },
  methods: {
      handleRemove(file, fileList) {
        console.log(file, fileList);
      },
      handlePreview(file) {
        console.log(file);
      },
      handleExceed(files, fileList) {
        this.$message.warning(`The limit is 3, you selected ${files.length} files this time, add up to ${files.length + fileList.length} totally`);
      },
      beforeRemove(file, fileList) {
        return this.$confirm(`Cancel the transfert of ${ file.name } ?`);
      }
    }
}
</script>
<style lang="scss">
.clientdeal {
  margin: 46px 0 0 5px;
  border: 1px rgb(38, 38, 38) solid;

  .head_clientdeal {
    background-color:  rgb(16,48,52);
    color: white;
    font-size: 14px;
    padding: 8px 0 3px 7px;

    .dash { padding: 0 5px 0 5px; }
  }

  .form_clientdeal {
    padding-left: 40px;
    color: rgb(97,97,97);

    #pad {
      padding: 0;
      margin: 0;
    }
    #file {
      width: 30%;
      border: none;
      background-color: rgb(27,27,27);
    }
    #upload_style {
      background-color: rgb(27,27,27);
      border: none;
      color: green;
      font-size: 14px;
    }

    #textarea {
    width: 86%;
    resize: none;
    border: 2px rgb(42,42,42) solid;
    background-color: rgb(31,31,31);
    padding: 12px;
    color: rgb(97,97,97);
    }
    #submit_clientdeal {
    background-color: rgb(31,31,31);
    border: 2px rgb(80,80,80) solid;
    border-radius: 3px;
    color: rgb(97,97,97);
    width: 27%;
    margin-left: 59%;
    padding: 0;
    }
  }
}
</style>
