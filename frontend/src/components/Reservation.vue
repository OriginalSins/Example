<template>
  <el-row class="reservation_form">
    <el-col>
      <el-form name="reservation">
          <el-form-item label="Квартира №">
            <el-input v-model="apartament" id="book" class="apartament" name="apartament" required></el-input>
          </el-form-item>
          <el-form-item label="Цена">
            <el-input v-model="price" id="book" class="price" name="price" required></el-input>
          </el-form-item>
        <el-form-item label="Тип оплаты">
          <select id="book" class="type" name="pay" v-model="selected">
            <option>Не выбран</option>
            <option value="100% оплата">100% оплата</option>
            <option value="Ипотека">Ипотека</option>
            <option value="Рассрочка">Рассрочка</option>
            <option value="Военная ипотека">Военная ипотека</option>
          </select>
        </el-form-item>
        <el-form-item label="temp">
          <span slot="label">Менеджер застройщика</span>
          <el-input v-model="manager" id="book" class="manager" name="manager"></el-input>
        </el-form-item>
        <el-form-item><p>КОМЕНТАРИЙ К БРОНИ</p></el-form-item>
        <el-form-item>
          <el-input type="textarea" :rows="5" v-model="textarea" id="textarea" name="comment"></el-input>
        </el-form-item>
        <el-form-item>
          <p>Статус:</p>
          <!-- <el-input type="submit" value="Назначить сделку" id="submit_reservation"></el-input> -->
          <el-button @click.prevent="onsubmit" id="submit_reservation">Назначить сделку</el-button>
        </el-form-item>
      </el-form>
    </el-col>
  </el-row>
</template>
<script>
export default {
  data() {
    return {
      textarea: '',
          apartament: '',
          price: '',
          manager: '',
          selected: ''
    }
  },
  methods: {
    onsubmit() {
      var price = this.price;
      var apartament = this.apartament;
      var manager = this.manager;
      var comment = this.textarea;
      var selected = this.selected;


      console.log('Цена:', price)
      console.log('Кваритра:', apartament)
      console.log('Менеджер:', manager)
      console.log('Коментарий:', comment)
      console.log('Тип оплаты:', selected)
    }
  }
}
</script>
<style lang="scss">
.reservation_form {
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

    #submit_reservation {
    background-color: rgb(31,31,31);
    border: 2px rgb(56, 84, 51) solid;
    border-radius: 3px;
    color: rgb(56, 84, 51);
    float: right;
    margin-right: 13%;
    padding: 10px;
    }

    #book {
      border: 2px rgb(42,42,42) solid;
      background-color: rgb(31,31,31);
    }

    .apartament { width: 17%; }

    .price { width: 35%; }

    .type {
      height: 36px;
      width: 50%;
      color: rgb(80,80,80);
    }

    .manager { width: 50%; }
  }
</style>
