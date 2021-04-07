<template>
  <div class="testTemplate">
    <div class="template__box">
      <h1 class="user-profile_username">@{{ user.username }}</h1>
      <div class="user-profile_oldschool_badge" v-if="user.isOldSchool">
        <strong>User status: Old school</strong>
      </div>
    </div>
    <div class="posts_list" v-if="user.number == 4">
    <ul id="example-1">
      <li class="items_in_list"  v-for="post in user.posts" :key="post.content">
        {{ post.content }}
      </li>
    </ul>
    </div>
    <button v-on:click="reverseMessage">Reverse username</button>

    <button v-on:click="changeUserStatus">Change user status</button>

    <button v-on:click="counter">Incrementer</button>
    {{user.number}}
  </div>
</template>

<script>
export default {
  name: "Test",
  data() {
    return {
      user: {
        id: 1,
        username: "TestTestarN",
        firstname: "förTest",
        lastname: "slutTest",
        isOldSchool: true,
        number: 0,
        posts: [
          { content: "Test1" },
          { content: "Test2" },
          { content: "Test3" },
          { content: "Test4" },
        ],
      },
    };
  },
  methods: {
    reverseMessage() {
      this.user.username = this.user.username.split("").reverse().join("");
    },
    changeUserStatus(){
      if(this.user.isOldSchool == true){
         this.user.isOldSchool = this.user.isOldSchool= false;
      }
      else
        this.user.isOldSchool = this.user.isOldSchool = true;
    },
    counter(){
      this.user.number++;
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
button{
  margin: 10px;
  font-size: 20px;
  border: solid 1px;
  border-color: green;
  cursor: pointer;
}
.items_in_list {
  border: 1px solid grey;
  margin: 10px;
  border-radius: 5px;
  font-weight: bold;
  margin-right: auto;
  display: grid;
  grid-template-columns: 1fr 3fr;
  grid-gap: 50px;
  padding: 50px 5%;
}
#example-1 {
  align-content: center;
  color: darkolivegreen;
  display: flex;
  flex-direction: column;
}
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
