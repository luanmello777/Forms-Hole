<template>
  <v-container class="mt-16 pt-5">
    <v-img height="100" src="/logo.png" />

    <div :class="smAndDown ? '' : 'ml-16'">
      <h2 :class="smAndDown ? '' : 'ml-16 pl-16'" class="text-secondary">Cadastre-se na holé</h2>
      <p class="text-terciary" :class="smAndDown ? '' : 'ml-16 pl-16'">Insira seus dados para acessar a plataforma Holé.
      </p>

      <div :class="smAndDown ? '' : 'ml-12 pl-16'">
        <v-form v-model="valid">
          <v-container>
            <v-row>
              <v-col cols="12" md="5">
                <v-text-field v-model="nome" :rules="nomeRules" label="Nome" color="#ff4f00" hint="Informe seu nome"
                  prepend-icon="mdi-account-circle-outline text-deep-orange-accent-3"></v-text-field>
              </v-col>

              <v-col cols="12" md="5">
                <v-text-field v-model="sobrenome" :rules="sobrenomeRules" label="Sobrenome" color="#ff4f00"
                  hint="Informe seu sobrenome"
                  prepend-icon="mdi-account-circle-outline text-deep-orange-accent-3"></v-text-field>
              </v-col>

              <v-col cols="12" md="5">
                <v-text-field v-model="Email" :rules="emailRules" label="Email" placeholder="email@email.com.br"
                  hint="Informe seu E-mail" color="#ff4f00"
                  prepend-icon="mdi-account-circle-outline text-deep-orange-accent-3"></v-text-field>
              </v-col>

              <v-col cols="12" md="5">
                <v-text-field v-model="Telefone" :rules="foneRules" label="Telefone" placeholder="(99) 9999-9999"
                  hint="Informe seu telefone" color="#ff4f00"
                  prepend-icon="mdi-cellphone text-deep-orange-accent-3"></v-text-field>
              </v-col>

              <v-col cols="12" md="5">
                <v-text-field v-model="Senha" :rules="senhaRules" label="Senha" color="#ff4f00" hint="Informe sua senha"
                  prepend-icon="mdi-form-textbox-password text-deep-orange-accent-3"></v-text-field>
              </v-col>

              <v-col cols="12" md="5">
                <v-text-field v-model="RepitirSenha" :rules="repitirsenhaRules" label="Repitir Senha" color="#ff4f00"
                  hint="Informe sua senha novamente"
                  prepend-icon="mdi-form-textbox-password text-deep-orange-accent-3"></v-text-field>
              </v-col>


            </v-row>
          </v-container>
          <v-checkbox v-model="checkbox" class="font2"
            label="Li e concordo com so Termos de Uso e Política de Privacidade." required></v-checkbox>
        </v-form>

        <div class="d-flex justify-center align-center" :class="smAndDown ? '' : 'mr-16'">
          <v-btn class="btn text-white" color="primary" width="750" height="45"
            :class="smAndDown ? '' : 'mr-16'">Cadastrar</v-btn>
        </div>
      </div>
    </div>
  </v-container>

  <br>
  <br>
  <br>

  <v-footer class="bg-quaternary d-flex justify-center align-center"
    :class="smAndDown ? 'pl-12 pr-12 ml-1 mr-1' : 'pt-5 pb-5'">
    <h5>Todos os Direitos Reservados ® - 2022 - BOMTUR VIAGENS E TURISMO LTDA. - CNPJ 05.663.682/0001-36</h5>
  </v-footer>
</template>

<style scoped>
.btn {
  border-radius: 15px;
}

.footer,
h5 {
  font-family: 'Exo 2', sans-serif;
  opacity: 0.8;
  font-size: 15px;
}
</style>

<script setup>
import { useDisplay } from 'vuetify';
import { ref } from 'vue';


const { smAndDown } = useDisplay()
const checkbox = ref(false);
const valid = ref(false);

const nome = ref('');
const nomeRules = ref([
  value => {
    if (value) return true;
    return 'É necessário inserir um nome.';
  },
  value => {
    if (value?.length <= 50) return true;
    return 'Insira um nome de no minimo 3 letras.';
  },
]);

const sobrenome = ref('');
const sobrenomeRules = ref([
  value => {
    if (value) return true;
    return 'É necessário inserir um Sobrenome.';
  },
  value => {
    if (value?.length <= 50) return true;
  },
]);

const Email = ref('');
const emailRules = ref([
  value => {
    if (value) return true;
    return 'É necessário inserir um E-mail.';
  },
  value => {
    if (/.+@.+\..+/.test(value)) return true;
    return 'E-mail deve ser válido.';
  },
]);

const Telefone = ref('');
const foneRules = ref([
  value => {
    if (value?.length <= 11) return true;
    return 'É necessário inserir um telefone.';
  },
  value => {
    if (/.+@.+\..+/.test(value)) return true;
    return 'O telefone deve ser válido.';
  },
]);

const Senha = ref('');
const senhaRules = ref([
  value => {
    if (value) return true;
    return 'É necessário inserir uma senha.';
  },
  value => {
    if (/.+@.+\..+/.test(value)) return true;
    return 'A senha deve ser válida.';
  },
]);

const RepitirSenha = ref('');
const repitirsenhaRules = ref([
  value => {
    if (value) return true;
    return 'É necessário repitir a senha.';
  },
  value => {
    if (/.+@.+\..+/.test(value)) return true;
    return 'A senha deve ser válida.';
  },
]);
</script>
