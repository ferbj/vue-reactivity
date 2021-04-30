<template>
  <table class="table table-striped table-bordered table-condensed">
    <thead class="text-center">
      <th class="w-25">Id</th>
      <th class="w-25">Title</th>
      <th class="w-25">Completed</th>
      <th class="w-25">Actions</th>
    </thead>
    <tbody>
      <tr v-for="item in items" :key="item.id" class="text-center">
        <td class="w-25">{{ item.id }}</td>
        <td class="w-25">{{ item.title }}</td>
        <td v-bind:class="{'alert-success':item.completed==true,'alert-danger':item.completed==false}" class="w-25" >
          <input type="checkbox" v-on:change="markComplete" v-model="item.completed" v-bind:checked="item.completed==true" />
        </td>
        <td>
          <button @click="delitem(item.id)">
            <i class="fa fa-trash" aria-hidden="true"></i>
          </button>
        </td>
      </tr>
    </tbody>
  </table>
</template>

<script>
export default {
  name: "List",
  props: ["items"], 

  methods: {
    markComplete: function() {
      this.items.completed = !this.items.completed;
    },
    delitem: function(item) {
      //this.items = data.filter(item => item.id !== id);
      this.$emit("del-item", item);
    }
  }
};
</script>
