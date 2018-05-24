<template>

<span>

    <login-template>

        <h2>Login</h2>

        <input type="text" placeholder="E-mail" value="">
        <input type="text" placeholder="Senha" value="">
        <button type="button" class="btn">Entrar</button>

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
