<template>
  <div class="wrapper-popup " v-bind:class="getClassPopup">
    <div class="rule">
      <h3>Luật chơi game</h3>
      <p>
        2 bên lần lượt sử dụng lượt để gieo con xúc sắc . Khi gieo được mặt 6
        điểm sẽ được chơi tiếp thêm 1 lượt và cộng dồn số diểm lại sau mỗi lượt
        chơi. Khi quay vào ô 1 nút sẽ bị phạt. <br />
        <button v-on:click="confirm" class="confirm">Da hieu</button>
      </p>
    </div>
  </div>
</template>
<script>
export default {
  name: "popup-rule",
  data() {
    return {};
  },
  methods: {
    confirm() {
        // truyen event ra App.vue
        console.log('confirm PopupRule.vue');
        this.$emit('handleConfirm')
    } 
  },
  props: {
    isOpenPopup: { type: Boolean, default: false }
  },
  computed: {
    getClassPopup: function() {
      return {
        "open-popup": this.isOpenPopup
      };
    }
  }
};
</script>
<style>
.wrapper-popup {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: rgba(0, 0, 0, 0.4);
  opacity: 0;
  visibility: hidden;
}
.wrapper-popup.open-popup {
  opacity: 1;
  visibility: visible;
}
.open-popup .rule {
  transform: translate(-50%, -50%) scale(1);
}
.rule {
  position: absolute;
  padding: 20px;
  background-color: blanchedalmond;
  width: 400px;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%) scale(1.2);
  font-family: Arial, Helvetica, sans-serif;
  transition: all 0.3s ease;
}
.rule h3 {
  margin-bottom: 14px;
}
.rule .confirm {
  border: 2px solid goldenrod;
  margin-top: 10px;
  padding: 7px 15px;
  cursor: pointer;
  font-weight: bold;
  transition: all 0.3s ease;
  /* cursor:row-resize; */
}
.rule .confirm:hover {
  background: green;
  color: honeydew;
}
/* css3 xay dung hieu ung zoom in -zoom out  */
</style>