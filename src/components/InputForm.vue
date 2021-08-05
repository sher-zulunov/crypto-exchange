<template>
  <div class="currenc-send">
    <form @submit.prevent="addBalance">
      <p class="tax">{{ service }} счёт {{ currenc }}</p>
      <p class="tax">Коммисия 5%</p>
      <input
        type="number"
        class="currenc-send-input"
        placeholder="сумма"
        name="balance"
        v-model.lazy.trim="balance"
        required
        min="0.003"
        max="1000"
      />
      <input
        class="currenc-send-input"
        type="text"
        :placeholder="address"
        required
      />

      <textarea
        name=""
        :id="id"
        cols="60"
        rows="2"
        placeholder="Комментарий"
      ></textarea>
      <div class="input-value-cont">
        <input :id="id" class="input-value" type="submit" value="Вывести" />
      </div>
    </form>
  </div>
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
