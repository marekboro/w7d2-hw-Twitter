
<template>
  <div>
    <section id="totalTweets">
      <p>Total Likes:{{totalLikes}}</p>
    </section>

    <section id="tweeting">
      <form v-on:submit.prevent="addTweet">
        <h4>Tweet a tweet</h4>
        <input placeholder="Your name" type="text" v-model="newTweet.name" />
        <input placeholder="Your handle" type="text" v-model="newTweet.handle" />
        <input placeholder="Your tweet" type="text" v-model="newTweet.tweet" />
        <input type="submit" value="Tweet" />
      </form>
    </section>
    <section id="Filter">
      <form v-on:submit.prevent="filterByLikes">
        <h4>Fileter by likes:</h4>
        <input type="number" v-model.number="likesFilterAmount" />
        <input type="submit" value="Filter" />
      </form>
    </section>
  
    <section>
      <tweet-list-item v-for="(tweet,index) in filterByLikes" :key="index" :tweetx="tweet"></tweet-list-item>
    </section>
  </div>
</template>

<script>
import TweetListItem from "./components/TweetListItem.vue";
export default {
  name: "App",
  data() {
    return {
      tweets: [
        {
          id: 1,
          name: "James",
          handle: "@jokerjames",
          img: "https://semantic-ui.com/images/avatar2/large/matthew.png",
          tweet: "If you don't succeed, dust yourself off and try again.",
          likes: 10,
        },
        {
          id: 2,
          name: "Fatima",
          handle: "@fantasticfatima",
          img: "https://semantic-ui.com/images/avatar2/large/molly.png",
          tweet: "Better late than never but never late is better.",
          likes: 12,
        },
        {
          id: 3,
          name: "Xin",
          handle: "@xeroxin",
          img: "https://semantic-ui.com/images/avatar2/large/elyse.png",
          tweet: "Beauty in the struggle, ugliness in the success.",
          likes: 18,
        },
      ],
      newTweet: {
        id: 0,
        name: "",
        handle: "",
        img: "https://semantic-ui.com/images/avatar2/large/elyse.png",
        tweet: "",
        likes: 0,
      },
      likesFilterAmount: 0,
    };
  },
  computed: {
    totalLikes: function () {
      return this.tweets.reduce((total, tweet) => {
        return total + tweet.likes;
      }, 0);
    },
    // filterByLikes: function(){
    //   return this.tweets.filter(tweet => tweet.likes >= this.likesFilterAmount)
    // }
    filterByLikes: function () {
      return this.tweets.filter((tweet) => {
       return tweet.likes >= this.likesFilterAmount;
      });
      this.likesFilterAmount = 0;
    },
  },
  components: {
    "tweet-list-item": TweetListItem,
  },
  methods: {
    addTweet: function () {
      this.tweets.unshift(this.newTweet);
      this.newTweet = {
        id: "",
        name: "",
        handle: "",
        img: "https://semantic-ui.com/images/avatar2/large/elyse.png",
        tweet: "",
        likes: 0,
      };
    },
  },
};
</script>

<style>
</style>