<template >
  <!-- <div v-for="friend in listFriends" :key="friend.id">
    Name: {{ friend.name }}      Age: {{ friend.age }}     id: {{ friend.id }}
  </div> -->
  <div style="padding: 10px">
    <ListFriend
      v-for="friend in listFriends"
      :key="friend.id"
      :modelValue="friend"
      @update:modelValue="updateUser"
      @deleleFriend="deleteFriend"
    >
    </ListFriend>
    <AddFriend @addFriend="addFriend"> </AddFriend>

    <br />
    <button @click="submitData">Submit</button>
  </div>
</template>

<script>
import ListFriend from "./components/ListFriend.vue";
import AddFriend from "./components/AddFriend.vue";

export default (await import("vue")).defineComponent({
  components: {
    ListFriend,
    AddFriend,
  },
  data() {
    return {
      listFriends: [
        {
          id: 1,
          name: "Thanh",
          age: 29
        },
        {
          id: 2,
          name: "Toai",
          age: 28
        },
        {
          id: 3,
          name: "Long",
          age: 30
        },
      ],
    };
  },
  methods: {
    updateUser(user) {
      let friendChange = this.listFriends.find((friend) => {
        return friend.id === user.id;
      });
      friendChange.name = user.name;
      friendChange.age = user.age;
    },
    deleteFriend(id) {
      this.listFriends = this.listFriends.filter((friend) => {
        return friend.id !== id;
      });
    },
    addFriend(user) {
      if (user.name && user.age) {
      let newId = 1
      for (let i = 0; i < this.listFriends.length; i++){
        let checkId = this.listFriends.some(friend => {
          return friend.id === newId
        })
        console.log(checkId)
      if (checkId) {
        newId++
      }
      }
        this.listFriends = [
          ...this.listFriends,
          { 
            ...user,
            id: newId,
          },
        ];
      }
    },
    submitData() {
      console.log(this.listFriends);
    },
  },
});
</script>
