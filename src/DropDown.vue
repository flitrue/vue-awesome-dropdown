<template>
  <div>
    <div class="drop-down" @click="handleClick" v-click-outside="handleClose">
      <div v-if="value" class="input">{{value}}</div>
      <div v-else class="placeholder">{{placeholder}}</div>
      <img class="arrow" src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADAAAAAwCAYAAABXAvmHAAABxElEQVRoQ+2VQUrDQBSG30sX7aa7UhEtknSK4hFciB7ApVdw566CeAPRpTu37vQSSvEEgouE0Ar2BEKhTTsSaSCUqJ38M0rhZT3vn//7/5eEacUfXnH/JAD/3aA0IA2ACcgKgQHC49IAHCEoIA2AAcLj0gAcISggDYABwuPGDQyHw8ZoNDqq1+v3zWbzA3YwFwjD8MDzvKTdbvdMNI0BwjB8ZeYdrXVcq9X2W63Wu8mFRWejKOoS0RUR6Uqlcuj7/uOymkYAWmuOouiFmXfnF7xVq9U9BCJn/kvS87zjIAgenACkonEcb0+n0x4zN1CIRfNEdKuUOlnWfHrOqIFMOIWYzWZpzWtlIQrM3yilTk3MlwZIBweDQTCZTJ7LQNgyDwGUhbBpHgYwhbBt3grAshAuzFsD+A2iwPy1UurM9IUtOl/qK/TdxUUvNhHdEdFFbsaaeasNZAYLIPK8Vs07AcjWaTwePzHzhqvkM12rK5SPOo7jrfkfe1NrfdnpdM5t7PyihjOA9KJ+v7+eJImvlEp/eE4epwBOHC+ICsBfpPzTHdKANAAmICsEBgiPSwNwhKCANAAGCI9LA3CEoIA0AAYIj38CGjO4MTLSkJYAAAAASUVORK5CYII=" alt="arrow">
      <transition name="fade">
        <div class="popper" v-show="visible">
          <div class="item" v-for="(item,index) in list" :key="index" @click="handleSelect(item)">{{item.name}}</div>
          <div class="center" v-show="list.length==0">列表为空</div>
        </div>
      </transition>
    </div>
  </div>
</template>

<script>
import { directive as clickOutside } from "./libs/v-click-outside-x.js";
export default {
  name: "DropDown",
  props: {
    value: {
      type: String,
      default: ""
    },
    list: {
      type: Array,
      default: function(){
        return []
      }
    }
  },
  directives: { clickOutside },
  data() {
    return {
      placeholder: "未选择",
      visible: false
    };
  },
  methods: {
    handleClick() {
      this.visible = !this.visible;
    },
    handleSelect(data) {
      this.$emit('input', data.name);
      this.$emit('on-change', data)
    },
    handleClose() {
      this.visible = false
    }
  }
};
</script>


<style lang="less" scoped>
.drop-down {
  display: inline-block;
  width: 100%;
  vertical-align: middle;
  background-color: rgba(255, 255, 255, 0.3);
  line-height: 30px;
  height: 30px;
  cursor: pointer;
  border-radius: 3px;
  color: #dcdcdc;
  position: relative;
  transition: all 0.5s ease-in-out;
  .input {
    padding-left: 12px;
    padding-right: 20px;
    font-size: .86rem;
  }
  .placeholder{
    padding-left: 12px;
    padding-right: 20px;
    font-size: .86rem;
  }
  .arrow {
    position: absolute;
    top: 6px;
    width: 20px;
    height: 20px;
    line-height: 1;
    right: 4px;
    transition: all 0.2s ease-in-out;
  }
  .popper{
    max-height: 200px;
    overflow: auto;
    position: absolute;
    width: 100%;
    z-index: 99;
    background-color: #1f1c1c;
    border-radius: 3px;
    padding: 5px 0;
    color: #dcdcdc;
    font-size: 13px;
    .item{
      padding: 0 10px;
      &:hover{
        background-color: #444;
        color: #dcdcdc;
      }
    }
    .center{
      text-align: center;
    }
  }
}
</style>
