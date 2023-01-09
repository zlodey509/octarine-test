<template>
  <header class="header">
    <div class="header__logo">
      <img :src="getImageUrl('header_logo.svg')" alt="">
      <span>box</span>
    </div>
    <div class="header__menu">
      <a v-for="(item, index) in menu_items" href="#" class="header__menu-item">
        {{item}}
      </a>
    </div>
    <div class="header__actions">
      <a v-for="index in header_icons_count" href="#" class="header__actions-item">
        <img :src="getImageUrl(`header_icon-${index}.svg`)" alt="">
      </a>
    </div>
  </header>

  <div class="advice">
    <div class="advice__content">
      <div class="advice__content-title">
        Zack Snyder's <br>
        Justice League
      </div>
      <div class="advice__content-info">
        <span>2021</span>
        <span class="border-info">18+</span>
        <span>4h 2min</span>
        <span id="advice__content-info__rating">
          8.8 
          <img :src="getImageUrl('star.svg')" alt="">
        </span>
      </div>
      <div class="advice__content-description">
        Determined to ensure Superman's ultimate sacrifice was not in vain, Bruce Wayne aligns forces with Diana Prince with plans to recruit a team of metahumans to protect the world from an approaching threat of catastrophic proportions.
      </div>
      <div class="advice__content-actions">
        <div class="button button-info advice__content-actions__item">
          <img :src="getImageUrl('play_icon.svg')" alt="">
          <span>Watch</span>
        </div>
        <div class="button advice__content-actions__item">
          More information
        </div>
      </div>
    </div>
    <div class="advice__photo">
      <img :src="getImageUrl('advice_photo.png')" alt="">
    </div>
  </div>

  <div class="trending">
    <div v-for='(type, index) in trending_types' class="trending__item">
      <div class="title">
        {{type.name}}
      </div>
      <div class="trending__item-photos_slide">
        <splide :options="trendingSlideOptions">
          <splide-slide v-for="index in type.photos_count">
            <img class="trending__item-photos_slide__photo" :src="getImageUrl(`${type.photo_prefix}_photo-${index}.png`)" alt="">
          </splide-slide>
        </splide>
      </div>
    </div>

    <div class="button button-info" style="display: inline-block;">
      See more
    </div>
  </div>

  <div class="genres">
    <div class="title">
      Popular Genres
    </div>
    <div class="genres__items">
      <div v-for="(genre, index) in genres" class="genres__items-item" :style="{ background: 'linear-gradient(' + genre.gradient +')' }">
        <div class="genres__items-item__content">
          <img :src="getImageUrl(`genres-${index+1}.svg`)" alt="">
          <div>{{genre.name}}</div>
        </div>
      </div>
    </div>
  </div>

  <div class="actors">
    <div class="title">
      Popular Actors & Directors
    </div>
    <div class="actors__items">
      <splide :options="actorsSlideOptions">
        <splide-slide v-for="(actor, index) in actors" class="actors__items-item">
          <img class="actors__items-item__photo" :src="getImageUrl(`actors-${index+1}.png`)" alt="">
          <div class="actors__items-item__name">{{actor}}</div>
        </splide-slide>
      </splide>
    </div>
  </div>

  <div class="coming_soon">
    <div class="coming_soon__photo">
      <img :src="getImageUrl('comingsoon_photo.png')" alt="">
    </div>
    <div class="coming_soon__content">
      <div class="coming_soon__content-photo">
        <img :src="getImageUrl('comingsoon_2021.png')" alt="">
      </div>
      <div class="coming_soon__content-text">
        Coming Soon...
      </div>
    </div>
  </div>

  <div class="register">
    <div class="register__text">
      Are You New Here ?
      <br>
      Don’t wait, Register Now.
    </div>
    <div class="register__button button button-info">
      Register Now
    </div>
  </div>

  <footer class="footer">
    <div class="footer__logo header__logo">
      <img :src="getImageUrl('header_logo.svg')" alt="">
      <span>box</span>
    </div>
    <div class="footer__blocks">
      <div v-for="(block, index) in footer_blocks" class="footer__blocks-block">
        <a v-for="(item, i) in block" href="#" class="footer__blocks-block__item">
          {{item}}
        </a>
      </div>
    </div>
  </footer>
</template>

<script>
  import { Splide, SplideSlide } from '@splidejs/vue-splide';
  import '@splidejs/splide/dist/css/themes/splide-default.min.css';

  export default{
     components: {
      Splide,
      SplideSlide,
    },
    data(){
      return{
        menu_items: ['Home', 'TV Shows', 'Movies', 'Series'],
        header_icons_count: 3,
        trending_types: [
          {
            name: 'Trending TV Shows',
            photo_prefix: 'shows',
            photos_count: 6,
          },
          {
            name: 'Trending Movies',
            photo_prefix: 'movies',
            photos_count: 6,
          },
        ],
        trendingSlideOptions: {
          rewind : true,
          type: 'loop',
          gap: '40px',
          fixedWidth: '200px',
          perMove: 1,
          pagination: false,
          arrows: false,
        },
        genres: [
          {
            name: 'Romance',
            gradient: '109.31deg, #FD093F 2.4%, #F383F1 100%'
          },
          {
            name: 'Drama',
            gradient: '114.5deg, #0FFFDA 2.22%, #3CDB77 68.84%'
          },
          {
            name: 'Historical',
            gradient: '109.31deg, #B936FF 2.4%, #57DEDA 100%'
          },
          {
            name: 'Action',
            gradient: '109.31deg, #FD093F 2.4%, #FB1378 2.41%, #FCCB1A 100%'
          },
          {
            name: 'Sci-fi',
            gradient: '109.31deg, #FF6472 2.4%, #FDA75D 100%'
          },
          {
            name: 'Sci-fi',
            gradient: '110.16deg, #13547A 2.37%, #80D0C7 96.77%'
          },
          {
            name: 'Comedy',
            gradient: '109.93deg, #FFF77B 2.37%, #FFBF42 50%'
          },
          {
            name: 'Documentary',
            gradient: '109.31deg, #1FA2FF 2.4%, #1FA2FF 2.41%, #1F535C 97.46%'
          },
        ],
        actors: ['Samantha Bowen', 'Rhys Birch', 'James Holloway', 'Joshua Walton', 'Patrick Elliott', 'Morgan O`Neill'],
        actorsSlideOptions: {
          rewind : true,
          type: 'loop',
          gap: '40px',
          fixedWidth: '190px',
          perMove: 1,
          pagination: false,
          arrows: false,
        },
        footer_blocks: [
          ['Voice over and Subtitle', 'Media Center', 'Privacy', 'Contact us'],
          ['Voice Description', 'Investor Relations', 'Legal Provisions',],
          ['Help Center', 'Job Opportunities', 'Cookies Preferences',],
          ['Gift Cards', 'Terms of Use', 'Corporate Informations',],
        ],
      }
    },
    mounted(){

    },
    methods:{
      getImageUrl(name){
              return new URL(`./assets/img/${name}`, import.meta.url).href
      },
    },
  }
</script>
