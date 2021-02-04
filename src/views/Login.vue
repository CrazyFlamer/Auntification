<template>
    <div class="d-flex justify-center">
        <v-card width="600px" class="mt-12 pa-10">
            <v-card-title>
                Войдите в аккаунт
            </v-card-title>

            <v-text-field
                label="Введите логин"
                v-model="login"
                outlined
            ></v-text-field>

            <v-text-field
                label="Введите пароль"
                v-model="password"
                outlined
            ></v-text-field>

            <v-btn @click="authenticate">
                Войти
            </v-btn>
        </v-card>
    </div>
</template>

<script>
  export default {
    data(){
      return{
        login: undefined,
        password: undefined,
        storage: '',
        myId: ''
      }
    },
    methods: {
      authenticate()
      {
        this.axios.get('http://37.77.104.246/api/jsonstorage/?id=539f8121b1571fa15c0bcb06318e6a89')
          .then(
            (response) => {
              let users = response.data;
              let found = false;
              for(let index in users){
                if(this.login == users[index].login && this.password == users[index].password){
                  this.$router.push('/users/' + this.myId);
                  found = true;
                  break;
                }
              }
              if(!found)
                  window.alert('hhhhhhhhhhhhhh')
            }
          )
      }
    }
  }
</script>

<style scoped>
  input{
    font-size: 30px;
    margin-top: 30px;
  }
  button{
    font-size: 30px;
    padding: 10px;
  }
</style>
