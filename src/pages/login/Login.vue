<template>

<span>

    <login-template>


      <span slot="menuesquerdo">
        <img src="https://static.quizur.com/i/b/5b035c77702c13.471891555b035c775c3ff9.54480388.png" class="responsive-img">
      </span>
      <span slot="principal">

            <h2>Login</h2>
            <input type="text" placeholder="E-mail" value="" v-model="email">
            <input type="password" placeholder="Senha" value="" v-model="password">
            <button  class="btn" v-on:click="login()">Entrar</button>
            <router-link to="/cadastro" class="btn orange">Cadastre-se</router-link>

      </span>
        

    </login-template>

</span>
</template>

<script>
import LoginTemplate from '@/templates/LoginTemplate'


export default {
  name: 'Login',
  components:{
    LoginTemplate
  },
  methods:{
  login(){
    console.log("ok");
    this.$http.post(this.$urlAPI+`login`,{
     email: this.email,
     password: this.password
    })
    .then(response => {
      //console.log(response)
      if(response.data.status){
        //login  com sucesso
        console.log('login com sucesso')
        this.$store.commit('setUsuario', response.data.usuario);
        sessionStorage.setItem('usuario',JSON.stringify(response.data.usuario));
        this.$router.push('/');
      }else if(response.data.status == false && response.data.validacao){
        console.log('erros de validação')
        let erros = '';
        for(let erro of Object.values(response.data.erros)){
          erros += erro +" ";
        }
        alert(erros);
        
      }else{
        //login não existe
        console.log('login não existe')
        alert('Login inválido!');
        
       }
    })
    .catch(e => {
    console.log(e)
    alert("Erro! Tente novamente mais tarde!")
    })
  }
  },
  data () {
    return {
     email:'',
     password:''
    }
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
