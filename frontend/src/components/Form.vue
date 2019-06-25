<template>
  <el-row class="forms">
    <el-col :span="24">
      <el-row class="head_form">
        <el-col :span="24">
          <span>ЖК {{ complex }}</span>
          <span class="dash">—</span>
          <span>{{ area }}</span>
          <span class="dash">—</span>
          <span>2.5%</span>
        </el-col>
      </el-row>
      <el-row class="center_form">
        <el-row  class="nav_form">
          <el-col :span="24">
            <el-col :span="8" :class="{active: activeLink === 1}"><a href="#" @click="switchView('Fixation')" @click.prevent="activeLink = 1">Фиксация</a></el-col>
            <el-col :span="8" :class="{active: activeLink === 2}"><a href="#" @click="switchView('Display')" @click.prevent="activeLink = 2">Показ</a></el-col>
            <el-col :span="8" :class="{active: activeLink === 3}"><a href="#" @click="switchView('Reservation')" @click.prevent="activeLink = 3">Бронь</a></el-col>
          </el-col>
        </el-row>
        <component :is="currentView"></component>
      </el-row>
    </el-col>
  </el-row>
</template>

<script>
import Fixation from './Fixation'
import Display from './Display'
import Reservation from './Reservation'

  export default {
    props: {
      client: Object,
      complex: String,
      area: String
    },
    data() {
      return {
        currentView: undefined,
        activeLink: undefined
      }
    },
    methods: {
      switchView(view) {
            this.currentView = view
          }
    },
    components: {
      Fixation,
      Display,
      Reservation
    }
  }
</script>

<style lang="scss">
.forms {
  margin: 46px 10px 0 4px;

  .head_form {
    div {
      padding: 8px 0 1px 9px;
      background-color: rgb(31,31,31);
      border: 1px rgb(38,38,38) solid;
      color: white;
      font-size: 15px;
    }
    .dash {
      padding: 0 5px 0 5px;
    }
  }
  .center_form {
    background-color: rgb(31,31,31);
    border: 1px rgb(38,38,38) solid;
    margin-top: 3px;

    .nav_form {
      padding-top: 15px;

      div {
        text-align: center;
      }

      a {
        background-color: rgb(31,31,31);
        color: rgb(97,97,97);
        border: none;
        font-size: 14px;
      }
      .active a {
        border-bottom: 3px #409EFF solid;
        display: block;
        padding-bottom: 10px;
        color: white;
      }
    }
  }
}
</style>
