<template lang="pug">
    footer
        div(
          v-for="red in networkSocials" 
          v-animate-css="animations.Jello"
          v-animate-css.hover="animations.Pulse"
          )
            a(v-if="red.url" :href="red.url" class="card-icon")
                img(
                  v-lazy="red.icon" 
                  alt="red.name" 
                  class="icons")
                h4 {{red.name}}
            div(v-else class="card-icon")
                img(v-lazy="red.icon" class="icons")
                h4 {{red.data}}

        
</template>

<script>
import email from "../assets/images/gmail-icon.png";
import github from "../assets/images/github-icon.png";
import linkendin from "../assets/images/linkedin-icon.png";
import twitter from "../assets/images/twitter-icon.png";
import youtube from "../assets/images/youtube-icon.png";

export default {
  name: "foot",
  data: function() {
    return {
      networkSocials: [
        // {
        //   name: "Telefono",
        //   icon: telephone,
        //   data: "3504459101"
        // },
        {
          name: "Email",
          icon: email,
          data: "jaalorsa519\n@gmail.com"
        },
        {
          name: "Youtube",
          icon: youtube,
          url: "https://www.youtube.com/channel/UC2629Jqdc0PQCYRxmF3fcZA"
        },
        {
          name: "Twitter",
          icon: twitter,
          url: "https://twitter.com/jaalorsa517"
        },
        {
          name: "Linkedin",
          icon: linkendin,
          url:
            "https://www.linkedin.com/in/jaime-alberto-ortiz-saldarriaga-54a3409b"
        },
        {
          name: "Github",
          icon: github,
          url: "https://github.com/jaalorsa517"
        }
      ],
      animations: {
        Jello: {
          classes: "jello"
        },
        Pulse: {
          classes: "pulse"
        }
      }
    };
  }
};
</script>

<style lang="stylus" scoped>
flex-display()
    display flex
    justify-content center
    align-items center

footer
    width 100%
    height 150px
    min-height 100px
    flex-display ()
    background #79D70F
a, h4
    font-size 1rem
    text-decoration none
.card-icon
    flex-display()
    flex-direction column
    margin 0 20px
.icons
    width 64px
    height 64px

@media screen and (max-width: 767px)
  footer
    height 100px
  a, h4
    font-size 0.5rem
  .card-icon
    width 32px
    margin 0 15px
  .icons
    width 32px
    height 32px

@media screen and (min-width: 768px) and (max-width: 1440px)
  footer
    height 100px
  a, h4
    font-size 0.8rem
  .card-icon
    width 48px
    margin 0 20px
  .icons
    width  48px
    height 48px
</style>
