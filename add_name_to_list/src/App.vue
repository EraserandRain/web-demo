<template>
  <div id="app">
    <input type="text" id="name" @keyup.enter="addInput" />
    <ul id="list">
      <li
        v-for="item in arr"
        :key="item.listNum"
        @click="switchRed"
        :class="{ red: item.isRed }"
      >
        {{ item.message }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      arr: [],
    };
  },
  methods: {
    switchRed() {
      if (this.arr[this.arr.listNum].isRed == false) {
        this.arr[this.arr.listNum].isRed = true;
      } else {
        this.arr[this.arr.listNum].isRed = false;
      }
    },
    addInput() {
      this.arr.push({
        listNum: this.arr.length,
        isRed: false,
        message: document.getElementById("name").value,
      });
      for (let i = 0; i < this.arr.length; i++) {
        console.log(this.arr[i]);
        console.log(this.arr[i].listNum + " and " + this.arr[i].message);
      }
      document.getElementById("name").value = "";
    },
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
#app {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  row-gap: 10px;
  margin: 20px;
}
#name {
  width: 300px;
}
.red {
  color: red;
}
</style>
