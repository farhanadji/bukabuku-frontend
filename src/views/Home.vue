<template>
  <div>
  <v-container grid-list-md>
    <v-subheader>
      Random Category 
      <v-spacer></v-spacer>
      <router-link to="/categories">See All</router-link>
    </v-subheader>

    <v-layout row wrap>
      <v-flex v-for="category in categories" xs6 :key="category.id">
        <v-card :to="'/category/'+ category.slug">
          <v-card-media
            :src="getImage('/'+category.image)"
            height="150px"
          >
            <v-container fill-height fluid pa-2>
              <v-layout fill-height>
                <v-flex xs12 align-end flexbox>
                  <span class="title white--text text-block" v-text="category.name"></span>
                </v-flex>
              </v-layout>
            </v-container>
          </v-card-media>

          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn icon>
              <v-icon>favorite</v-icon>
            </v-btn>
            <v-btn icon>
              <v-icon>bookmark</v-icon>
            </v-btn>
            <v-btn icon>
              <v-icon>share</v-icon>
            </v-btn>
          </v-card-actions>

        </v-card>
      </v-flex>
    </v-layout>
  </v-container>

  <v-container grid-list-md>
    <v-subheader>
      Top Books 
      <v-spacer></v-spacer>
      <router-link to="/books">See All</router-link>
    </v-subheader>
    <v-layout row wrap>
      <v-flex
        v-for="(book, index) in books" xs6 :key="index">
        <v-card :to="'/book/'+ book.slug">
          <v-card-media
            :src="getImage('/'+book.cover)"
            height="150px"
          >
            <v-container fill-height fluid pa-2>
              <v-layout fill-height>
                <v-flex xs12 align-end flexbox>
                  <span class="title white--text text-block" v-text="book.title"></span>
                </v-flex>
              </v-layout>
            </v-container>
          </v-card-media>

          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn icon>
              <v-icon>favorite</v-icon>
            </v-btn>
            <v-btn icon>
              <v-icon>bookmark</v-icon>
            </v-btn>
            <v-btn icon>
              <v-icon>share</v-icon>
            </v-btn>
          </v-card-actions>
        </v-card>
      </v-flex>
    </v-layout>
  </v-container>
  </div>
</template>
<style scoped>
.text-block {
    position: absolute;
    bottom: 5px;
    left: 5px;
    background-color: black;
    padding-left: 5px;
    padding-right: 5px;
    opacity: 0.7;
    width:100%;
}
</style>

<script>
export default {
  data: () => ({
    categories: [],
    books: []
  }),
  methods: {
  
  },
  created(){
    let count = 4
    this.axios.get('/categories/random/'+count)
        .then((response) => {
            let categories = response.data.data
            this.categories = categories
        })
        .catch((error) => {
            let responses = error.response
            console.log(responses)
        })

    count = 8
    this.axios.get('/books/top/'+count)
        .then((response) => {
            let books = response.data.data
            this.books = books
        })
        .catch((error) => {
            let responses = error.response
            console.log(responses)
        })
  }
}
    var Tawk_API=Tawk_API||{}, Tawk_LoadStart=new Date();
    (function(){
    var s1=document.createElement("script"),s0=document.getElementsByTagName("script")[0];
    s1.async=true;
    s1.src='https://embed.tawk.to/5d06100d36eab9721117aeae/default';
    s1.charset='UTF-8';
    s1.setAttribute('crossorigin','*');
    s0.parentNode.insertBefore(s1,s0);
    })();
</script>