<template>
  <div id="app">
    <form action="" v-if="flag">
      <label for="email">Email</label>
      <input type="email" v-model="form.email" id="email" class="form-control">

      <label for="fName">First Name</label>
      <input type="text" v-model="form.fName" id="fName" class="form-control">

      <label for="lName">Last Name</label>
      <input type="text" v-model="form.lName" id="lName" class="form-control">

      <label for="telephone">telephone</label>
      <input type="text" v-model="form.phone" id="telephone" class="form-control">

      <button type="button" class="btn btn-primary mt-10" @click="addGuest">+</button>
      <ul>
        <li v-for="(guest, key) in guests" :key="key">
          <label for="guest" @click="deleteGuest">Гость  {{key + 1}} </label>
          <input type="text" id="guest" class="form-control" v-model="guests[key]">
        </li>
      </ul>
      <hr>
    <button type="submit" class="btn btn-success mt-10" @click.prevent="onSubmit">Send</button>
    </form>
    <table class="table table-striped" v-else>
      <tr>
        <td>Email</td>
        <td>{{form.email}}</td>
      </tr>
      <tr>
        <td>Name</td>
        <td>{{fullName}}</td>
      </tr>
      <tr>
        <td>Phone</td>
        <td>{{form.phone}}</td>
      </tr>
      <tr>
        <td>Guests</td>
        <td>
          <table class="table">
            <tr class="list-group-item" v-for="(guest, key) in guests " :key="key">
             <td>{{key}}</td>
              <td>{{guest}}</td>
            </tr>
          </table>
        </td>
      </tr>
    </table>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'app',
  data() {
    return {
      flag: true,
      form: {
        email: '',
        fName: '',
        lName: '',
        phone: ''
      },
      guests: []
    }
  },
  methods: {
    onSubmit () {
      this.flag = false
    },
    addGuest () {
      this.guests.push('')
    },
    deleteGuest () {
      this.guests.pop()
    }
  },
  computed: {
    fullName () {
      return this.form.fName + ' ' + this.form.lName
    }
  },
  components: {
  }
}
</script>

<style>
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
