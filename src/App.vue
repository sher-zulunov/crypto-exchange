<template>
  <div id="app">
    <div class="container">
      <h1>Currencies exchange</h1>
      <div class="currenc-container">
        <currenc-button
          :currenc="this.btc"
          :balance="this.balance"
        ></currenc-button>
        <currenc-button
          :currenc="this.doge"
          :balance="this.balance"
        ></currenc-button>
        <currenc-button :currenc="this.ltc"></currenc-button>
        <input-form />
        <currenc-button :currenc="this.shib"></currenc-button>
        <currenc-button :currenc="this.bnb"></currenc-button>
        <currenc-button :currenc="this.usd"></currenc-button>
        <currenc-button :currenc="this.rur"></currenc-button>
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
      balance: 0.0,
    };
  },
};
</script>
