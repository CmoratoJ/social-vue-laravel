<template>

<span>

    <login-template>


      <span slot="menuesquerdo">
        <img src="https://static.quizur.com/i/b/5b035c77702c13.471891555b035c775c3ff9.54480388.png" class="responsive-img">
      </span>
      <span slot="principal">

         <h2>Cadastro</h2>
            <input type="text" placeholder="Nome" v-model="name">
            <input type="text" placeholder="E-mail" v-model="email">
            <input type="password" placeholder="Senha" v-model="password">
            <input type="password" placeholder="Confirme sua senha" v-model="password_confirmation">
            <button type="button" class="btn" v-on:click="cadastro()">Enviar</button>
            <router-link to="/login" class="btn orange">Já sou cadastrado</router-link>
      </span>
        

    </login-template>

</span>
</template>

<script>
import LoginTemplate from '@/templates/LoginTemplate'


export default {
  name: 'Cadastro',
  components:{
    LoginTemplate
  },
  methods:{
  cadastro(){
    console.log("ok");
    this.$http.post(this.$urlAPI+`cadastro`,{
      name: this.name,
      email: this.email,
      password: this.password,
      password_confirmation: this.password_confirmation
    })
    .then(response => {
      //console.log(response)
      if(response.data.status){
        //login  com sucesso
        console.log('cadastro realizado com sucesso')
        this.$store.commit('setUsuario', response.data.usuario);
        sessionStorage.setItem('usuario',JSON.stringify(response.data.usuario));
        this.$router.push('/');
      }else if(response.data.status == false && response.data.validacao){
        //erros de validação
        console.log('erros de validação')
        let erros = '';
        for(let erro of Object.values(response.data.erros)){
          erros += erro +" ";
        }
        alert(erros);
        
      }else{
        //login não existe
        alert('Erro no cadastro! Tente novamente mais tarde.');
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
      name:'',
      email:'',
      password:'',
      password_confirmation:''
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
