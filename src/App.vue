<template>
  <div id="app">
    <div class="container">
      <h1>Currencies exchange</h1>
      <div class="currenc-container">
        <currenc-button
          :currenc="this.btc"
          :balance="this.balancebtc"
          @input-balance="toggleInputForm"
          @withdraw-balance="toggleWithdrawForm"
        ></currenc-button>
        <currenc-button
          :currenc="this.doge"
          :balance="this.balancedoge"
        ></currenc-button>
        <currenc-button
          :currenc="this.ltc"
          :balance="this.balanceltc"
        ></currenc-button>
        <div v-show="isInput" class="currenc-send">
          <input-form @add-balance="addBalance"></input-form>
        </div>
        <currenc-button
          :currenc="this.shib"
          :balance="this.balanceshib"
        ></currenc-button>
        <currenc-button
          :currenc="this.bnb"
          :balance="this.balancebnb"
        ></currenc-button>
        <currenc-button
          :currenc="this.usd"
          :balance="this.balanceusd"
        ></currenc-button>
        <currenc-button
          :currenc="this.rur"
          :balance="this.balancerur"
        ></currenc-button>
      </div>
    </div>
  </div>
</template>

<script>
import CurrencButton from "./components/CurrencButton.vue";
import InputForm from "./components/InputForm.vue";

export default {
  name: "App",
  components: {
    CurrencButton,
    InputForm,
  },
  data() {
    return {
      btc: "BTC",
      doge: "DOGE",
      ltc: "LTC",
      shib: "SHIB",
      bnb: "BNB",
      usd: "USD",
      rur: "RUR",
      balancebtc: 0,
      balancedoge: 0,
      balanceltc: 0,
      balanceshib: 0,
      balancebnb: 0,
      balanceusd: 0,
      balancerur: 0,
      isInput: false,
    };
  },
  methods: {
    toggleInputForm() {
      this.isInput = !this.isInput;
    },
    toggleWithdrawForm() {
      this.isInput = !this.isInput;
    },
    addBalance(balance) {
      this.balancebtc += Number(balance);
      console.log("2");
    },
  },
};
</script>
