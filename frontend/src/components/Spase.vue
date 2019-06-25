<template>
  <div>
    <el-row class="header">
      <el-col :span="18">
        <span class="logo"><img src="/images/logo1.png" class="logoimg" alt="logo"/><p class="colorp">Ag</p><p>enz</p></span>
      </el-col>
      <el-col :span="6" class="profile">
        <el-col :span="2" class="bell"><button></button></el-col>
        <el-col :span="2" class="avatar"><img src="/images/img_prof.jpg" id="img_prof"></el-col>
        <el-col :span="11" class="user"><p>{{ userName }}</p></el-col>
        <el-col :span="2" class="exit"><a href="#" id="exit" @click="logout"><img src="/images/exit1.png"></a></el-col>
      </el-col>
    </el-row>

    <el-row class="container">
      <el-col class="navigation">
        <ul class="nav">
          <li v-for="item in routes">
            <router-link :to="{ name: item.url }" class="router-link">
              <el-col><el-col :id="item.itemid"></el-col></el-col>
              <p>{{ item.label }}</p>
            </router-link>
          </li>
        </ul>
      </el-col>
      <el-col class="info">
        <router-view></router-view>
      </el-col>
    </el-row>
  </div>
</template>

<script>
  import {
    HOME,
    DEAL,
    TO_PAY,
    FINISH,
    TARIFFS
  } from '../routes'

  export default {
    data() {
      return {
        userName: "Дмитрий Власов",
        routes: [
          {
            img: "/images/1.png",
            label: "В РАБОТЕ",
            url: HOME,
            itemid: "work"
          },
          {
            img: "/images/4.png",
            label: "НА СДЕЛКЕ",
            url: DEAL,
            itemid: "deal"
          },
          {
            img: "/images/3.png",
            label: "НА ОПЛАТЕ",
            url: TO_PAY,
            itemid: "topay"
          },
          {
            img: "/images/2.png",
            label: "ЗАВЕРШЕННЫЕ",
            url: FINISH,
            itemid: "finish"
          },
          {
            img: "/images/5.png",
            label: "ТАРИФЫ",
            url: TARIFFS,
            itemid: "tariffs"
          }
        ]
      }
    },
    methods: {
      logout() {
        console.log('LOGOUT')
      }
    }
  }
</script>

<style lang="scss">

  .header {
    background-color: #1a1a1a;
    height: 50px;

    .logo {
      display: grid;
      grid-template-columns: 39% 25% 36%;
      width: 90px;
      margin: 10px 0 0 5px;

      .logoimg {
        width: 32px;
        height: 32px;
      }
      .colorp { color: #2c97de; }
      p {
        font-size: 17px;
        padding-top: 5px;
        color: white;
      }
    }


    #img_prof {
      width: 20px;
      height: 20px;
    }

    #exit img {
      width: 23px;
      height: 23px;
    }

    .profile {
      margin-top: 14px;

      .bell { margin-right: 25px; }
      .avatar { margin-right: 10px; }
      .user {
        margin-right: 25px;
        text-align: center;
      }
      .exit { margin-right: 15px; }

      button {
        border: none;
        padding: 0;
        background: url('/images/bells.png') no-repeat 0 0;
        background-size: 17px;
        width: 17px;
        height: 17px;
      }

      p {
        font-size: 12px;
        color: #444444;
      }

      a {
        text-decoration: none;
        display: inline-block;
      }
    }
  }

  .container {
     display: flex;

    .navigation {
      text-align: center;
      background-color: #1a1a1a;
      max-width: 10.2%;

      #work {
        background: url('/images/work.png') no-repeat 0 0;
        height: 41px;
        background-position: center;
        margin: 10px 0 6px 0;
      }
      #deal {
        background: url('/images/deal.png') no-repeat 0 0;
        height: 41px;
        background-position: center;
        margin: 10px 0 6px 0;
      }
      #topay {
        background: url('/images/topay.png') no-repeat 0 0;
        height: 41px;
        background-position: center;
        margin: 10px 0 6px 0;
      }
      #finish {
        background: url('/images/finish.png') no-repeat 0 0;
        height: 41px;
        background-position: center;
        margin: 10px 0 6px 0;
      }
      #tariffs {
        background: url('/images/tariffs.png') no-repeat 0 0;
        height: 41px;
        background-position: center;
        margin: 10px 0 6px 0;
      }

  .nav li { list-style: none; }
  .nav .router-link {
    display: block;
    height: 87px;
  }
  .nav img {
    width: 42px;
    padding-top: 10px;
  }
  .nav p {
    color: #5c5c5c;
    font-size: 12px;
  }
  #finish { padding-top: 10px; }
    }

    .nav a.router-link-active, li.router-link-active > a {
      background-color: #232323;
      display: block;
      border-left: 3px #2c97de solid;

        #work {
          background: url('/images/workactive.png') no-repeat 0 0;
          background-position: center;
        }
        #deal {
          background: url('/images/dealactive.png') no-repeat 0 0;
          background-position: center;
        }
        #topay {
          background: url('/images/topayactive.png') no-repeat 0 0;
          background-position: center;
        }
        #finish {
          background: url('/images/finishactive.png') no-repeat 0 0;
          background-position: center;
        }
        #tariffs {
          background: url('/images/tariffsactive.png') no-repeat 0 0;
          background-position: center;
        }
        p { color: #f2f2f2; }
    }

    .info {
      background-color: #242424;
      min-height: 100vh;
      width: 89.8%;
    }
  }

</style>
