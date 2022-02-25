<template>
  <b-container>
    <b-row align-h="center" class="text-start">
      <b-col class="mt-5 col-md-5">
        <h4>Faça a converção de valores</h4>
        <label>Valor a ser convertido</label>
        <b-input-group
          class="mb-4"
          :prepend="code + ' - $'"
          v-if="code == 'USD'"
        >
          <b-form-input
            :state="valorAConverter.validation"
            v-model="valorAConverter.valor"
            type="text"
          ></b-form-input>
          <b-button variant="primary" @click="converter()">Converter</b-button>
        </b-input-group>

        <b-input-group
          class="mb-4"
          :prepend="code + ' - €'"
          v-if="code == 'EUR'"
        >
          <b-form-input
            :state="valorAConverter.validation"
            v-model="valorAConverter.valor"
            type="text"
          ></b-form-input>
          <b-button variant="primary" @click="converter()">Converter</b-button>
        </b-input-group>

        <label>Valor em reais</label>
        <b-input-group prepend="BR - R$" class="mb-3">
          <b-form-input v-model="valorConvertido" disabled> </b-form-input>
        </b-input-group>
      </b-col>
    </b-row>
  </b-container>
</template>

<script>
export default {
  name: "Form",

  props: {
    ask: String,
    code: String,
  },

  data: function () {
    return {
      valorAConverter: {
        valor: null,
        validation: null,
      },
      valorConvertido: "0,00",
      mensagemDeErro: "",
    };
  },

  methods: {
    converter() {
      this.valorConvertido = (this.ask * this.valorAConverter.valor)
        .toFixed(2)
        .replace(".", ",");

      this.valorAConverter.validation = this.isValidate(
        this.valorAConverter.valor
      );
    },

    isValidate: function (valor) {
      if (!isNaN(parseFloat(valor))) {
        return true;
      }
      this.valorConvertido = "[Apenas valor numérico]";
      return false;
    },
  },
};
</script>

<style>
</style>