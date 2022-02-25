<template>
  <b-container>
    <b-row align-h="center">
      <b-col cols="3" class="mt-5">
        <b-card class="text-center bg-light mb-4">
          <b-card-text class="mt-3">
            <h2>R$ {{ Number(ask.valor).toFixed(2).replace(".", ",") }}</h2>
          </b-card-text>
          <b-card-text
            >Cotação do
            <strong>
              {{ code.valor }}
            </strong>
            hoje
          </b-card-text>

          <b-card-text>Moeda:</b-card-text>
          <b-form-select
            v-model="moedaSelecionada"
            :options="options"
            @change="getMoeda()"
          >
          </b-form-select>
        </b-card>
      </b-col>
    </b-row>
  </b-container>
</template>

<script>
export default {
  name: "Card",

  data: function () {
    return {
      moedaSelecionada: "USD-BRL",
      moedas: [],

      ask: {
        valor: "",
      },

      code: {
        valor: "",
      },

      options: [
        { value: "USD-BRL", text: "USD (Dolar Americano)" },
        { value: "EUR-BRL", text: "EUR (Euro)" },
      ],
    };
  },

  props: {
    getSelectedMoeda: Function,
  },

  methods: {
    getMoeda: async function () {
      const result = await fetch(
        "https://economia.awesomeapi.com.br/json/last/" + this.moedaSelecionada
      )
        .then((res) => res.json())
        .then((res) => res)
        .catch((error) => {
          return {
            error: true,
            message: error,
          };
        });

      if (!result.error) {
        if (result.USDBRL) {
          this.ask.valor = result.USDBRL.ask;
          this.code.valor = result.USDBRL.code;
        }

        if (result.EURBRL) {
          this.ask.valor = result.EURBRL.ask;
          this.code.valor = result.EURBRL.code;
        }

        this.moedas = result;
      }
    },
  },

  created: function () {
    this.getMoeda();
  },

  updated: function () {
    this.getSelectedMoeda(this.moedas);
  },
};
</script>

<style>
</style>