<template>
  <div id="app">
    <div class="wrapper">

    <div class="progress">
      <div class="progress-bar" role="progressbar" :style="progressStyles"  aria-valuemin="0" aria-valuemax="100"></div>
    </div>
    <form action="" v-if="flag" @submit.prevent="onSubmit" @input="validateAll">
      <label for="email">{{info[0].name}}</label>
      <i class="fa " :class="{'fa-ban': !info[0].flag,'fa-check-circle': info[0].flag}" v-show="info[0].display"></i>
      <input type="email"  @input="validateEmail" v-model="info[0].value" id="email" class="form-control">

      <label for="name">{{info[1].name}}</label>
      <i class="fa " :class="{'fa-ban': !info[1].flag,'fa-check-circle': info[1].flag}" v-show="info[1].display"></i>
      <input type="text" @input="validateName" v-model="info[1].value" id="name" class="form-control">

      <label for="telephone">{{info[2].name}}</label>
      <i class="fa " :class="{'fa-ban': !info[2].flag,'fa-check-circle': info[2].flag}" v-show="info[2].display"></i>
      <input type="text" @input="validatePhone" v-model="info[2].value" id="telephone" class="form-control">

      <label for="some1">{{info[3].name}}</label>
      <i class="fa " :class="{'fa-ban': !info[3].flag,'fa-check-circle': info[3].flag}" v-show="info[3].display"></i>
      <input type="text" @input="validateField1" v-model="info[3].value" id="some1" class="form-control">

      <label for="some2">{{info[4].name}}</label>
      <i class="fa " :class="{'fa-ban': !info[4].flag,'fa-check-circle': info[4].flag}" v-show="info[4].display"></i>
      <input type="text" @input="validateField2" v-model="info[4].value" id="some2" class="form-control">

    <button type="submit" class="btn btn-success pt-10" :disabled="!done" @click="flag=!flag">Send</button>
    </form>
      <div class="table-wrapper" v-else>
        <table class="table table-striped" >
          <tr>
            <td>Email</td>
            <td>{{this.info[0].value}}</td>
          </tr>
          <tr>
            <td>Name</td>
            <td>{{this.info[1].value}}</td>
          </tr>
          <tr>
            <td>Phone</td>
            <td>{{this.info[2].value}}</td>
          </tr>
          <tr>
            <td>Some Field 1</td>
            <td>{{this.info[3].value}}</td>
          </tr>
          <tr>
            <td>Some Field 2</td>
            <td>{{this.info[4].value}}</td>
          </tr>
        </table>
        <button class="btn btn-dark" @click="flag=!flag">Назад</button>
      </div>

  </div>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'app',
  data() {
    return {
      done: false,
      flag: true,
      progress: 0,
      info: [
        {
          name: 'Email',
          value: '',
          pattern: /.+/,
          flag: false,
          display: false
        },
        {
          name: 'Name',
          value: '',
          pattern: /^[a-zA-Z ]{3,30}$/,
          flag: false,
          display: false
        },
        {
          name: 'Phone',
          value: '',
          pattern: /^[0-9]{7,14}$/,
          flag: false,
          display: false
        },
        {
          name: 'Some Field 1',
          value: '',
          pattern: /.+/,
          flag: false,
          display: false
        },
        {
          name: 'Some Field 2',
          value: '',
          pattern: /.+/,
          flag: false,
          display: false
        }
      ]
    }
  },
  methods: {
    validateName() {
      if(this.info[1].pattern.test(this.info[1].value)) {
        this.info[1].flag = true;
        this.info[1].display = true;
      } else if(!this.info[1].value.length) {
        this.info[1].display = false;
        this.info[1].flag = false;
      } else {
        this.info[1].flag = false;
        this.info[1].display = true;
      }


    },
    validateEmail() {
      if(this.info[0].pattern.test(this.info[0].value)) {
        this.info[0].flag = true;
        this.info[0].display = true;
      } else if(!this.info[0].value.length) {
        this.info[0].display = false;
        this.info[0].flag = false;
      } else {
        this.info[0].flag = false;
        this.info[0].display = true;
      }


    },
    validatePhone() {
      if(this.info[2].pattern.test(this.info[2].value)) {
        this.info[2].flag = true;

      } else if(!this.info[2].value.length) {
        this.info[2].display = false;
      } else {
        this.info[2].flag = false;
        this.info[2].display = true;
      }
    },
    validateField1() {
      if(this.info[3].pattern.test(this.info[3].value)) {
        this.info[3].flag = true;
        this.info[3].display = true;
      } else if(!this.info[3].value.length) {
        this.info[3].display = false;
        this.info[3].flag = false;
      } else {
        this.info[3].flag = false;
        this.info[3].display = true;
      }
    },
    validateField2() {
      if(this.info[4].pattern.test(this.info[4].value)) {
        this.info[4].flag = true;
        this.info[4].display = true;
      } else if(!this.info[4].value.length) {
        this.info[4].display = false;
        this.info[4].flag = false;
      } else {
        this.info[4].flag = false;
        this.info[4].display = true;
      }
    },
    validateAll() {
      if (this.info[0].flag
        && this.info[1].flag
        && this.info[2].flag
        && this.info[3].flag
        && this.info[4].flag) {
        this.done = true
      } else {
        this.done = false
      }



    }
  },
  computed: {
    progressStyles() {
      let d = 0;
      let that = this;
      for (let i of that.info) {
        if(i.flag) {
          d++;
        }
      }
      return {
        width: (d * 20) + '%'
      };
    }
  },
  components: {}
}
</script>

<style>
  .wrapper {
    max-width: 500px;
    width: 100%;
  }
  ul {
    list-style-type: none;
    padding: 0;
  }
  #input-group-1 {
    max-width: 500px;
  }
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  display: flex;
  justify-content: center;
}
</style>
