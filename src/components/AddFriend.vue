<template>
  <div style="padding-top: 30px;">
    <input
      type="text"
      placeholder="Name..."
      :value="user.name"
      @input="inputName"
    />
    <input
      type="text"
      placeholder="Age..."
      :value="user.age"
      @input="inputAge"
    />
    <button @click="addFriend">Add</button>
  </div>
</template>

<script lang="ts" se>
interface User {
  name: string;
  age: number;
}
export default (await import("vue")).defineComponent({
  data() {
    return {
      user: {
        name: "",
        age: "",
      },
    };
  },
  methods: {
    inputName(event: Event) {
      this.user.name = (event.target as HTMLInputElement).value;
    },
    inputAge(event: Event) {
      this.user.age = (event.target as HTMLInputElement).value;
    },
    addFriend() {
      this.$emit("addFriend", this.user);
      this.user.name = "";
      this.user.age = "";
    },
  },
});
</script>