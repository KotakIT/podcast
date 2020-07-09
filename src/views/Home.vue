<template>
  <div class="row justify-content-center">
    <div class="col-lg-5">
      <div class="container px-5 pt-3 bg-dark">
        <Header
          :description="rssData.description[0]"
          :image="rssData.image[0].url[0]"
          :title="rssData.title[0]"
        />
        <br />
        <iframe
          :src="
            'https://anchor.fm/kotakit/embed/episodes/' +
              rssData.item[0].link[0].replace(
                'https://anchor.fm/kotakit/episodes/',
                ''
              )
          "
          height="110"
          width="100%"
          frameborder="0"
          scrolling="no"
        ></iframe>
        <div
          class="text-center mb-5"
          v-html="rssData.item[0].description[0]"
        ></div>
        <div class="list-group">
          <router-link
            :to="
              'episode' +
                rssData.item[0].link[0].replace(
                  'https://anchor.fm/kotakit/episodes/',
                  ''
                )
            "
            v-for="episode in rssData.item"
            :key="episode.index"
            class="list-group-item list-group-item-action"
          >
            {{ episode.title[0] }}
          </router-link>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import Header from "@/components/Header.vue";
export default {
  name: "Home",
  components: {
    Header,
  },
  data() {
    return {
      rssData: [],
    };
  },
  methods: {
    async cek() {
      var parseString = require("xml2js").parseString;
      // var self = this;
      axios.get("https://anchor.fm/s/1217ef64/podcast/rss").then((res) => {
        parseString(res.data, (err, result) => {
          this.rssData = result.rss.channel[0];
        });
      });
    },
  },
  created() {
    this.cek();
  },
};
</script>
