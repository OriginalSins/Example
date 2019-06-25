<template>
  <el-row class="deal">
    <el-col :span="12">
      <el-row>
        <el-col :span="14">
          <h2>Найдено клиентов на сделке: {{ total }}</h2>
        </el-col>
      </el-row>
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
      <div>
        <el-row v-for="(item, key) in list" :key="key" class="list">
          <el-col :span="10">
            <a @click="selectClient(key, item.complex, item.area)" class="client_name">{{ item.name }}</a>
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
    <el-col :span="10" v-if="selectedClient != null">
      <info :complex="selectedClientComplex" :area="selectedClientArea"></info>
    </el-col>
  </el-row>
</template>
<script>
import ClientDeal from './ClientDeal'

export default {
  data() {
    return {
      list: [
        { name: 'Анатолий Полено', phone: '+380987788999', email: 'poleno@gmail.com', complex: 'FUTURIST', area: 'Северный город' },
        { name: 'Елена Полено', phone: '+380986677888', email: 'poleno-e@gmail.com', complex: 'Дом Полено', area: 'Где-то там' },
        { name: 'Гена Букин', phone: '+380981234567', email: 'Boookiin@gmail.com', complex: 'Bokin-house', area: 'Новый Мелитополь' }
      ],
      selectedClient: null,
      selectedClientComplex: '',
      selectedClientArea: ''
    }
  },
  methods: {

    selectClient(key, complex, area) {
      console.log('SELECT CLIENT ' + key)

      this.selectedClient = key
      this.selectedClientComplex = complex
      this.selectedClientArea = area
    }
  },

  components: {
    "info": ClientDeal
  },
  computed: {
    total() {
      return this.list.length;
    }
  }
}
</script>
<style lang="scss">
.deal {
  padding: 15px 0 0 30px;

  h2 {
  color: rgb(97, 97, 97);
  font-size: 22px;
  }

  .hat {
    margin-top: 20px;

    div {
      border: 1px rgb(38, 38, 38) solid;
      color: rgb(97,97,97);
      padding: 8px 0 2px 6px;
      font-size: 14px;
      background-color: rgb(31,31,31);
    }
  }
  .list {
    div {
      border: 1px rgb(38, 38, 38) solid;
      text-align: center;
      padding-top: 12px;
      word-break: break-all;
      height: 50px;
      margin-top: 3px;
      font-size: 14px;
      background-color: rgb(31,31,31);
    }
    .client_name {
      color: rgb(90, 106, 115);
    }
    .client_data {
      color: rgb(97,97,97);
    }
  }
}
</style>
