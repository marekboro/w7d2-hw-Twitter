<template>
  <div>
    <!-- <h3>Tweet List Item</h3> -->
    <li>
      <div id="avatarNameAndHandle">
        <img v-bind:src="tweetx.img" width="100px" height="100px" alt="avatar image" />
        <div>
          <p>{{tweetx.name}}</p>
          <p>{{tweetx.handle}}</p>
        </div>
      </div>
      <div id="tweet">
        <p>{{tweetx.tweet}}</p>
      </div>
      <div :class="likesStyling">
        <p> Likes: {{tweetx.likes}}</p>
      </div>
    </li>
  </div>
</template>

<script>
export default {
  name: "tweet-list-item",
  props: ["tweetx"],
  computed:{
      likesStyling: function(){
          return this.tweetx.likes>=10 ? "overTenLikes":"underTenLikes"
      }
  }
};
</script>

<style scoped>

li{
    background-color: antiquewhite;
    list-style: none;
    width: 23%;
    padding: 5px;
    margin:10px;
}
#avatarNameAndHandle{
    display: flex;
    flex-direction: row;
    padding: 0%;
    margin: 0%;
}
#avatarNameAndHandle > div {
    
    background-color: rgb(227, 248, 151);
    width: 100%;
    font-size:150%;
    height: 100px;
    display: flex;
    flex-direction: column;
    /* flex-flow: initial; */
}


#tweet {
background-color: cornsilk;
font-size: 130%;
}
.underTenLikes {
    background-color: rgb(97, 234, 252);

}
.overTenLikes {
    background-color: rgb(11, 228, 11);

}
p{
    margin: 0;
    padding: 0;
}

</style>