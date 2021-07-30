<template>
  <form @submit.prevent="addBalance">
    <input
      type="number"
      class="currenc-send-input"
      placeholder="сумма"
      name="balance"
      v-model.lazy.trim="balance"
    />
    <input class="currenc-send-input" type="text" placeholder="адрес" />
    <p class="tax">Коммисия 5%</p>
    <textarea
      name=""
      id=""
      cols="70"
      rows="2"
      placeholder="Комментарий"
    ></textarea>
    <div class="input-value-cont">
      <input id="balance" class="input-value" type="submit" value="Ввести" />
    </div>
  </form>
</template>
<script>
export default {
  name: "InputForm",
  methods: {
    addBalance() {
      if (this.balance === 0) {
        return;
      }
      this.$emit("add-balance", this.balance);
      this.balance = null;
    },
  },
  data() {
    return {
      balance: null,
    };
  },
};
</script>
