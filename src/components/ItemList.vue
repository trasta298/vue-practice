<template>
  <div>
    <div>
      <label>
        タスク
        <input type="text" v-model="newItemName" />
      </label>
      <label>
        期限
        <input type="text" v-model="newItemtime" />
      </label>
      <button @click="addItem">追加</button>
    </div>
    <table align="center" width="80%">
      <thead>
        <tr>
          <th>タスク</th>
          <th>期限</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="item in items" :key="item.status">
          <td>{{ item.name }}</td>
          <td>{{ item.time }}</td>
          <td v-if="item.status == 0">
            <button @click="completeTask(item)">完了</button>
          </td>
          <td v-if="item.status == 1">完了済み</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: "ItemList",
  data() {
    return {
      items: [],
      newItemName: "",
      newItemtime: ""
    };
  },
  methods: {
    addItem() {
      if (this.newItemName == "" || this.newItemtime == "") {
        alert("タスクと期限を追加してください！");
        return;
      }
      this.items.push({
        name: this.newItemName,
        time: this.newItemtime,
        status: 0,
      });
      this.newItemName = "";
      this.newItemtime = "";
      this.items.sort(function(a,b){
        if(a.status < b.status) return -1;
        if(a.status > b.status) return 1;
        return 0;
      });
    },
    completeTask(item) {
      item.status = 1;
      this.items.sort(function(a,b){
        if(a.status < b.status) return -1;
        if(a.status > b.status) return 1;
        return 0;
      });
    }
  }
};
</script>

<style>
.table {
  margin: auto;
}
</style>