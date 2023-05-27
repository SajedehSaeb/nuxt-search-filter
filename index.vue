<template>
    <v-row class="d-flex justify-center pt-3" >
      <v-col cols="12" md="6">
        <v-text-field v-model="search" @keypress="filter" solo placeholder="search..."></v-text-field>
        <v-row>
          <!-- <v-btn @click="Html" value="1">html</v-btn> -->
          <div v-for="item in buttonList" class="text-center">
            <v-btn color="white" class="btn" @click="select(item)">{{ item }}</v-btn>
          </div>
        </v-row>
      </v-col>
      <v-col cols="12" md="8">
        <v-row>
          <v-col cols="12" md="3" v-for="item in filterList" v-if="display">
            <v-card class="mx-auto pt-4 px-4 pb-4 text-center" >
              <v-img
                :src="item.src"
                height="200"
                cover
              ></v-img>

              <h3>
                {{ item.name }}
              </h3>
            </v-card>
          </v-col>
        </v-row>
        <v-row>
          <v-col cols="12" md="3" v-for="item in webcDesign" v-if="displaybtn">
            <v-card class="mx-auto pt-4 px-4 pb-4 text-center" >
              <v-img
                :src="item.src"
                height="200"
                cover
              ></v-img>

              <h3>
                {{ item.name }}
              </h3>
            </v-card>
          </v-col>
        </v-row>
      </v-col>
    </v-row>
</template>

<script>

  export default{
    data(){
      return{
        search : '',
        display : true,
        displaybtn : true,
        buttonList : ['all' , 'html' , 'vuetify' , 'vueJs'],
        webcDesign : [],
        webDesign: [
          {
            name: 'html',
            src : 'https://cdn-icons-png.flaticon.com/512/732/732212.png',
          },
          {
            name: 'css',
            src : 'https://cdn.icon-icons.com/icons2/1488/PNG/512/5351-css3_102605.png'
          },
          {
            name: 'javascript',
            src : 'https://upload.wikimedia.org/wikipedia/commons/thumb/9/99/Unofficial_JavaScript_logo_2.svg/512px-Unofficial_JavaScript_logo_2.svg.png',
          },
          {
            name: 'vueJs',
            src : 'https://upload.wikimedia.org/wikipedia/commons/f/f1/Vue.png',
          },
          {
            name: 'react',
            src : 'https://www.datocms-assets.com/45470/1631110818-logo-react-js.png',
            // src : 'https://upload.wikimedia.org/wikipedia/commons/thumb/a/a7/React-icon.svg/1200px-React-icon.svg.png'
          },
          {
            name: 'angular',
            src : 'https://upload.wikimedia.org/wikipedia/commons/thumb/c/cf/Angular_full_color_logo.svg/1200px-Angular_full_color_logo.svg.png',
          },
          {
            name: 'typescript',
            src : 'https://www.datocms-assets.com/48401/1627663113-learn-typescript.png?fit=max&w=900',
          },
          {
            name: 'jQuery',
            src : 'https://www.interviewbit.com/blog/wp-content/uploads/2021/10/jquery-logo-vertical_large_square.png'
          },
          {
            name: 'bootstrap',
            src: 'https://www.drupal.org/files/styles/grid-3-2x/public/project-images/bootstrap5.jpeg?itok=wkBtyvSM'
          },
          {
            name: 'vuetify',
            src : 'https://styles.redditmedia.com/t5_3nu8v/styles/communityIcon_ueewexj8rzu91.png',
          },
          {
            name: 'tailwind',
            src : 'https://upload.wikimedia.org/wikipedia/commons/thumb/d/d5/Tailwind_CSS_Logo.svg/2048px-Tailwind_CSS_Logo.svg.png',
          },

        ],
      }
    },

    computed:{
      filterList(){
        return this.webDesign.filter(course => {
          return course.name.toLowerCase().includes(this.search.toLowerCase())
        })
      },
    },



    methods : {
      filter(e){
        if(e.key){
          this.displaybtn = false
          this.display = true
        }
      },

      select(item){
        console.log(item)
        if(item == 'all'){
          this.displaybtn = true,
          this.search = '',
          this.webcDesign = this.webDesign
        }else{
          this.display = false,
          this.displaybtn = true,
          this.search = '',
          this.webcDesign = this.webDesign.filter(e => {
          return e.name == item;
        })
        }
      },
      // React(){
      //   console.log('react')
      //   this.webDesign = this.webDesign.filter(e => {
      //     return e.name == 'react';
      //   })
      // },

      // select(){
      //   console.log(this.value)
      // }
    }
  }
</script>

<style scoped>

.btn{
  border-radius: 5rem;
  color: rgb(0, 0, 0);
  margin: .3rem;
}
</style>


