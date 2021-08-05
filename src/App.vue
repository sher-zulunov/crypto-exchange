<template>
  <div id="app">
    <div class="container">
      <h1>Currencies exchange</h1>
      <div class="tab">
        <currenc-button
          :currenc="Btc.label"
          :balance="Btc.balance"
          @toggle-input="toggleInputFormBtc"
          @toggle-output="toggleOutputFormBtc"
        ></currenc-button>
        <currenc-button
          :currenc="Doge.label"
          :balance="Doge.balance"
          @toggle-input="toggleInputFormDoge"
        ></currenc-button>
        <currenc-button
          :currenc="Ltc.label"
          :balance="Ltc.balance"
          @toggle-input="toggleInputFormLtc"
        ></currenc-button>
      </div>
      <div class="tab">
        <input-form
          :service="accept"
          :currenc="Btc.label"
          v-if="this.Btc.isInput"
          @add-balance="addBalanceBtc"
          :address="address"
          :id="id"
        ></input-form>
      </div>
      <div class="tab">
        <input-form
          :service="send"
          :currenc="Btc.label"
          v-if="this.Btc.isOutput"
          @add-balance="withdrawBalanceBtc"
          :address="details"
          :id="id"
        ></input-form>
      </div>
      <div class="tab">
        <input-form
          v-if="this.Doge.isInput"
          @add-balance="addBalanceDoge"
          :id="id"
        ></input-form>
      </div>
      <div class="tab">
        <input-form
          v-if="this.Ltc.isInput"
          @add-balance="addBalance"
        ></input-form>
      </div>
      <div class="tab">
        <currenc-button @toggle-input="toggleInputForm"></currenc-button>
        <currenc-button></currenc-button>
        <currenc-button></currenc-button>
      </div>
      <div class="tab">
        <input-form v-show="isInput"></input-form>
      </div>
    </div>
  </div>
</template>

<script>
import CurrencButton from "./components/CurrencButton.vue";
import InputForm from "./components/InputForm.vue";
import uniqueId from "lodash.uniqueid";

export default {
  name: "App",
  components: {
    CurrencButton,
    InputForm,
  },
  data() {
    return {
      Btc: {
        id: uniqueId("ff-"),
        label: "BTC",
        balance: 0,
        commission: 1.05,
        isInput: false,
        isOutput: false,
      },
      Doge: { id: uniqueId("ff-"), label: "DOGE", balance: 0, isInput: false },
      Ltc: { id: uniqueId("ff-"), label: "LTC", balance: 0, isInput: false },
      Shib: { id: uniqueId("ff-"), label: "SHIB", balance: 0, isInput: false },
      Bnb: { id: uniqueId("ff-"), label: "BNB", balance: 0, isInput: false },
      Usd: { id: uniqueId("ff-"), label: "USD", balance: 0, isInput: false },
      Rur: {
        id: uniqueId("ff-"),
        label: "RUR",
        balance: 0,
        isInput: false,
        isOutput: false,
      },
      address: "Адрес",
      details: "Реквизиты",
      accept: "Ввести на ",
      send: "Вывести на ",
    };
  },
  methods: {
    toggleInputFormBtc() {
      this.Btc.isOutput ^= this.Btc.isOutput;
      this.Btc.isInput = !this.Btc.isInput;
    },
    toggleOutputFormBtc() {
      this.Btc.isInput ^= this.Btc.isInput;
      this.Btc.isOutput = !this.Btc.isOutput;
    },
    addBalanceBtc(balance) {
      let amount = Number(balance) / this.Btc.commission;
      return (this.Btc.balance += amount);
    },
    withdrawBalanceBtc(balance) {
      let amount = Number(balance) / this.Btc.commission;
      return (this.Btc.balance -= amount);
    },

    toggleInputFormDoge() {
      this.Doge.isInput = !this.Doge.isInput;
    },

    addBalanceDoge(balance) {
      this.Doge.balance += Number(balance);
      console.log("2");
    },
  },
};
</script>
