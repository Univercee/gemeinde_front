<template>
  <div class="signup">
    <router-link class="btn btn-outline-primary back-btn stiky" :to="{ name: 'index'}" role="button">{{$t('signup_1')}}</router-link>
    <div class="signup-wrapper">
      <header>
        <logo></logo>
      </header>
      <main v-if="!is_auth">
        <emailLogin></emailLogin><!-- TODO merge with verify -->
        <div class="divider">
          <hr/><span>{{$t('signup_2')}}</span><hr />
        </div>
        <div id="sso">
          <tgLogin></tgLogin>
        </div>
      </main>
      <main v-else class="w-100">
        <p class="mb-2 text-center">{{$t('signup_3')}}</p>
        <router-link class="nav-item btn btn-success w-100 mb-3" :to="{ name: 'profile'}">{{ $t('signup_4') }}</router-link>
      </main>
    </div>
    <div class="shifter"></div>
  </div>
</template>
<i18n>
{
  "en":{
    "signup_1":"Back",
    "signup_2":"or",
    "signup_3":"You are logged in",
    "signup_4":"My profile",
  },
  "de":{
    "signup_1":"Back",
    "signup_2":"oder",
    "signup_3":"You are logged in",
    "signup_4":"My profile"
  }
}
</i18n> 
<script id="vuescript">
  import tgLogin from '@/components/tgLogin.vue'
  import emailLogin from '@/components/emailLogin.vue'
  import logo from '@/components/logo.vue'
  import { defineComponent } from 'vue'
  import { mapGetters } from 'vuex';
 export default defineComponent({
    components: {
      tgLogin,
      emailLogin,
      logo
    },
    computed:{
      ...mapGetters('user',[
        'is_auth'
      ])
    }
  });
</script>
<style scoped>
  .signup {
    width: 100vw;
    height: 100vh;
    display: flex;
    background: url(../assets/images/signinup.jpg) no-repeat center center fixed;
    -webkit-background-size: cover;
    -moz-background-size: cover;
    -o-background-size: cover;
    background-size: cover;
    overflow: auto;
  }
  .signup-wrapper {
    background-color: rgba(0, 0, 0, 0.5);
    color: #fff;
    border-radius: 5px;
    margin: auto;
    padding: 20px;
    width: 25%;
    min-width: 300px;
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  .signup header{
    margin-bottom: 1em;
  }
  .signup header a{
    text-decoration: none;
  }
  .divider {
    margin-top: 2em;
    width: 100%;
    text-align: center;
  }

  .divider span {
    padding: 0 20px;
    font-size: 16px;
    position: relative;
    top: -0.6em;
  }

  .divider hr {
    display: inline-block;
    width: 33%;
  }

  #sso {
    text-align: center;
  }

  .back-btn{
    position: absolute;
    top: 10px;
    left: 10px;
    height: max-content;
  }

  .shifter{
    width: 0;
  }

  @media(min-width: 768px) {
  .shifter{
    width: 35%;
  } 
  }
</style>

