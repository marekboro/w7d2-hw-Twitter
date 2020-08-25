<template>
  <div>
    <!-- <h3>Tweet List Item</h3> -->
    <li>
      <div id="avatarNameAndHandle">
        <img v-bind:src="tweetx.img" width="100px" height="100px" alt />
        <div>
          <p>{{tweetx.name}}</p>
          <p>{{tweetx.handle}}</p>
        </div>
      </div>
      <div>
        <p>{{tweetx.tweet}}</p>
      </div>
      <div>
        <p>{{tweetx.likes}}</p>
      </div>
    </li>
  </div>
</template>

<script>
export default {
  name: "tweet-list-item",
  props: ["tweetx"],
};
</script>

<style scoped>

li{
    background-color: antiquewhite;
    list-style: none;
}
#avatarNameAndHandle{
    display: flex;
    flex-direction: row;
}
#avatarNameAndHandle > div {
    padding: 0;
    margin: 0;
}
</style>