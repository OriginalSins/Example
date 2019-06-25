<template>
  <el-row class="list_client">
    <el-col :span="12">

      <el-row>
        <el-col :span="14">
          <h2>Найдено клиентов в работе: {{ total }}</h2>
        </el-col>
        <el-col :span="10" class="new_client">
          <el-button @click="clientFormVisible = true" type="primary" icon="el-icon-plus" circle id="btn_new"></el-button>
          <span class="add_new">Добавить нового</span>
        </el-col>
      </el-row>

      <el-form :inline="true" :model="clientForm" v-if="clientFormVisible">
        <el-form-item>
          <el-input v-model="clientForm.name" :placeholder="labels.name" id="input_clientForm"></el-input>
        </el-form-item>
        <el-form-item>
          <el-input v-model="clientForm.phone" :placeholder="labels.phone" id="input_clientForm"></el-input>
        </el-form-item>
        <el-form-item>
          <el-input v-model="clientForm.email" :placeholder="labels.email" id="input_clientForm"></el-input>
        </el-form-item>
        <el-form-item>
          <el-button type="primary" @click="addClient" icon="el-icon-circle-plus"></el-button>
        </el-form-item>
      </el-form>

      <el-row class="hat">
        <el-col :span="10">
          <span class="">Имя клиента</span>
        </el-col>
        <el-col :span="7">
          <span>Телефон</span>
        </el-col>
        <el-col :span="7">
          <span>E-mail</span>
        </el-col>
      </el-row>

      <div v-if="total > 0">
        <el-row v-for="(item, key) in list" :key="key" class="list">
          <el-col :span="10">
            <a @click="selectClient(key)" class="client_name">{{ item.name }}</a>
          </el-col>
          <el-col :span="7">
            <a href="#" class="client_data">{{ item.phone }}</a>
          </el-col>
          <el-col :span="7">
            <a href="#" class="client_data">{{ item.email }}</a>
          </el-col>
        </el-row>
      </div>

    </el-col>

    <el-col :span="4" v-if="selectedClient != null">
      <house-complex v-on:house-chosen="selectHouseComplex"></house-complex>
    </el-col>

    <el-col :span="8" v-if="selectedHouseComplex != null">
      <aaa :client="list[selectedClient]" :complex="selectedHouseComplexName" :area="selectedHouseComplexArea"></aaa>
    </el-col>

  </el-row>
</template>

<script>
  import HouseComplex from './HouseComplex'
  import Form from './Form'

  export default {
    data() {
      return {
        labels: {
          name: "Ф.И.О.",
          phone: "Телефон",
          email: "Email",
          submit: "Добавить"
        },
        clientFormVisible: false,
        clientForm: {
          name: "",
          phone: "",
          email: ""
        },
        total: 0,
        list: [],

        selectedClient: null,
        selectedHouseComplex: null,
        selectedHouseComplexName: '',
        selectedHouseComplexArea: ''
      }
    },
    methods: {
      addClient() {
        if (this.clientForm.name !== '' &&
          this.clientForm.phone !== '' &&
          this.clientForm.email !== '') {

          let obj = {
            name: this.clientForm.name,
            phone: this.clientForm.phone,
            email: this.clientForm.email,
          };

          this.list.unshift(obj)
          this.total = this.list.length

          this.clientFormVisible = false;
          this.clientForm.name = '';
          this.clientForm.phone = '';
          this.clientForm.email = '';
        }
      },
      selectClient(key) {
        console.log('SELECT CLIENT ' + key)

        this.selectedClient = key
      },
      selectHouseComplex(key, name, area) {
        console.log('SELECT HOUSE ' + key)

        this.selectedHouseComplex = key
        this.selectedHouseComplexName = name
        this.selectedHouseComplexArea = area
      },
    },
    components: {
      HouseComplex,
      "aaa": Form
    }
  }
</script>

<style lang="scss" scoped>

.list_client {
  padding: 29px 0 0 42px;

  h2 {
  color: rgb(97, 97, 97);
  font-size: 20px;
  }

  .new_client {
    padding-left: 50px;
  }

  #btn_new {
    background-color: rgb(27,27,27);
    padding: 3px;
    font-size: 10px;
    color: #409EFF;
  }

  .add_new { color: #409EFF; }

  .hat {
    margin-top: 29px;

    div {
      border: 1px #2d2d2d solid;
      color: #747474;
      padding: 8px 0 2px 6px;
      font-size: 10px;
      background-color: #242424;
    }
  }
  .list {
    div {
      border: 1px #2d2d2d solid;
      text-align: center;
      padding-top: 12px;
      word-break: break-all;
      height: 50px;
      margin-top: 3px;
      font-size: 12px;
      background-color: #242424;
    }
    .client_name {
      color: #81b9df;
    }
    .client_data {
      color: #797878;
    }
  }
}
</style>
