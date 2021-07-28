<template>
  <transition name="fade">
    <div v-if="show" class="currenc-send">
      <input
        type="number"
        class="currenc-send-input"
        placeholder="сумма"
        name="balance"
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
        <input
          id="balance"
          @click="updateBalance"
          class="input-value"
          type="submit"
          value="Ввести"
        />
      </div>
    </div>
  </transition>
</template>
<script>
export default {
  name: "InputForm",
};
</script>
