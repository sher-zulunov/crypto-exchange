<template>
  <form @submit.prevent="addBalance">
    <p>{{ service }} счёт {{ currenc }}</p>
    <input
      type="number"
      class="currenc-send-input"
      placeholder="сумма"
      name="balance"
      v-model.lazy.trim="balance"
      required
    />
    <input
      class="currenc-send-input"
      type="text"
      :placeholder="address"
      required
    />
    <p class="tax">Коммисия 5%</p>
    <textarea
      name=""
      :id="id"
      cols="70"
      rows="2"
      placeholder="Комментарий"
    ></textarea>
    <div class="input-value-cont">
      <input :id="id" class="input-value" type="submit" value="Вывести" />
    </div>
  </form>
</template>
<script>
export default {
  name: "InputForm",
  props: {
    address: { required: true, type: String },
    comments: { required: true, type: String },
    id: { required: true, type: String },
    service: { required: true, type: String },
    currenc: { required: true, type: String },
  },
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
