<template>
  <div id="app">
    <h1>Type name and mark who is student</h1>
    <input type="text" id="name" @keyup.enter="addInput" />
    <ul id="list">
      <li
        v-for="item in arr"
        :key="item.listNum"
        @click="switchRed(arr.indexOf(item))"
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
    switchRed(item) {
      if (this.arr[item].isRed == false) {
        this.arr[item].isRed = true;
      } else {
        this.arr[item].isRed = false;
      }
    },
    addInput() {
      this.arr.push({
        listNum: this.arr.length,
        isRed: false,
        message: document.getElementById("name").value,
      });
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
