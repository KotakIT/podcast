<template>
  <main>
    <div class="row justify-content-center">
      <div class="col-lg-4 col-md-5 col-sm-8">
        <div class="container  pt-3 bg-dark">
          <Header
            :description="rssData.description[0]"
            :image="rssData.image[0].url[0]"
            :title="rssData.title[0]"
          />
          <br />
          <iframe
            v-if="this.$route.params.slug"
            :src="
              'https://anchor.fm/kotakit/embed/episodes/' +
                this.$route.params.slug
            "
            height="110"
            width="100%"
            frameborder="0"
            scrolling="no"
          ></iframe>
          <iframe
            v-else
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
            v-if="this.$route.params.slug"
            class="text-center mb-5"
            v-html="rssData.item[this.$route.params.item].description[0]"
          ></div>
          <div
            v-else
            class="text-center mb-5"
            v-html="rssData.item[0].description[0]"
          ></div>
          <div class="list-group pb-5">
            <router-link
              :to="
                '/episode/' +
                  episode.link[0].replace(
                    'https://anchor.fm/kotakit/episodes/',
                    ''
                  ) +
                  '/' +
                  index
              "
              v-for="(episode, index) in rssData.item"
              active-class="active"
              :key="episode.index"
              class="list-group-item list-group-item-action"
            >
              {{ episode.title[0] }}
            </router-link>
          </div>
        </div>
      </div>
    </div>
    <Footer />
  </main>
</template>
<style scoped>
.list-group-item.active {
  background-color: #8940fa;
  border-color: #8940fa;
}
</style>
<script>
import axios from "axios";
import Header from "@/components/Header.vue";
import Footer from "@/components/Footer.vue";
export default {
  name: "Home",
  components: {
    Header,
    Footer,
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
