<template>
  <div>
    <div
      v-for="(item, index) in computedNumber"
      :key="index"
      class="real-time-num"
      :style="{ background: background }"
    >
      <div
        class="real-time-num-item"
        :style="{
          transform:
            item !== ','
              ? `translateY(-${item * 40}px)`
              : `translateY(-${10 * 40}px)`,
          transition: `all ${speed}s ease-out`,
        }"
      >
        <div>0</div>
        <div>1</div>
        <div>2</div>
        <div>3</div>
        <div>4</div>
        <div>5</div>
        <div>6</div>
        <div>7</div>
        <div>8</div>
        <div>9</div>
        <div>,</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    number: {
      type: [Number, String],
      default: 0,
    },
    isSemicolon: {
      type: Boolean,
      default: true,
    },
    speed: {
      type: Number,
      default: 1,
    },
    background: {
      type: String,
      default: "#0e68cc",
    },
  },
  data() {
    return {
      computedNumber: [],
    };
  },
  watch: {
    number() {
      this.setComputedList();
      setTimeout(() => {
        this.genData();
      }, 0);
      this.$emit("numberChange", this.number);
    },
  },
  created() {
    this.setComputedList();
    setTimeout(() => {
      this.genData();
    }, 0);
  },
  computed: {
   
  },
  methods: {
    setComputedList() {
      this.string2List(this.number).forEach((item) => {
        this.computedNumber.push(0);
      });
    },
    genData() {
      this.computedNumber = this.string2List(this.number);
    },
    reset() {
      this.computedNumber = [0];
    },
    string2List(str) {
      const list = [];
      const res = [...String(str)].reverse();
      let currentIndex = 1;
      res.forEach((item, index) => {
        list.push(item);
        currentIndex++;
        if (this.isSemicolon) {
          if (currentIndex === 4 && index != res.length - 1) {
            list.push(",");
            currentIndex = 1;
          }
        }
      });
      list.reverse();
      return list;
    },
  },
};
</script>
