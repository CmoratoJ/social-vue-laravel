<template>

<span>

    <login-template>


      <span slot="menuesquerdo">
        <img src="https://static.quizur.com/i/b/5b035c77702c13.471891555b035c775c3ff9.54480388.png" class="responsive-img">
      </span>
      <span slot="principal">
        <h2>Login</h2>

        <input type="text" placeholder="E-mail" value="">
        <input type="text" placeholder="Senha" value="">
        <button type="button" class="btn">Entrar</button>
      </span>
        

    </login-template>

</span>
</template>

<script>
import LoginTemplate from '@/templates/LoginTemplate'
import CardConteudoVue from '@/components/social/CardConteudoVue'
import CardDetalheVue from '@/components/social/CardDetalheVue'
import PublicarConteudoVue from '@/components/social/PublicarConteudoVue'


export default {
  name: 'Login',
  components:{
    LoginTemplate,
    CardConteudoVue,
    CardDetalheVue,
    PublicarConteudoVue
  },
  data () {
    return {
      
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
