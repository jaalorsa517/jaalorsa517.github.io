<template lang="pug">
div
  nav.navegator
    a(
      v-for="(section,i) in sections"
      :key="i" 
      @mouseover="inHover(i)" 
      @mouseleave="outHover(i)" 
      @click="goTo(i)"
      href="#"
      v-animate-css="animations.Pulse"
      v-animate-css.hover="animations.Pulse"
      )
        transition(name="fade")
          .item-complete(v-show="section.hover" ) {{section.name}}
        .item(ref="item") {{section.init}}
                      
</template>

<script>
export default {
  name: "navi",
  data: function() {
    return {
      sections: [
        { name: "Básica", hover: false, init: 1 },
        { name: "Experiencia", hover: false, init: 2 },
        { name: "Estudios", hover: false, init: 3 }
      ],
      index_active: 0,
      animations: {
        Pulse: {
          classes: "pulse",
          delay: 200
        }
      }
    };
  },
  methods: {
    inHover: function(i) {
      this.$refs.item[i].classList.add("active");
      this.sections[i].hover = true;
    },
    outHover: function(i) {
      this.$refs.item[i].classList.remove("active");
      this.sections[i].hover = false;
    },
    goTo: function(i) {
      this.$refs.item[this.index_active].classList.remove("current");
      this.$refs.item[i].classList.add("current");
      this.index_active = i;
      switch (i) {
        case 0:
          if (this.$router.currentRoute.path !== "/") {
            this.$router.push({ name: "basic" });
          }
          break;
        case 1:
          if (this.$router.currentRoute.path !== "/experiencie") {
            this.$router.push({ path: "/experiencie" });
          }
          break;
        case 2:
          if (this.$router.currentRoute.path !== "/studies") {
            this.$router.push({ path: "/studies" });
          }
          break;
      }
    },
  },
  mounted: function() {
    this.$refs.item[this.index_active].classList.add("current");
  },
};
</script>

<style lang="stylus" scoped>
.fade-enter-active, .fade-leave-active
  transition: opacity 1s

.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */
  opacity: 0

.navegator
  margin 0
  & a
    display flex
    align-items center
    justify-content flex-end
    font-size 2rem
    text-decoration none
    text-align center

.item
    width 48px
    height 48px
    margin 15px
    margin-left 0
    line-height 1.5
    border-radius 50%
    background-color #F5A31A
    transition 0.5s
  &.active
    border-top-left-radius 0
    border-bottom-left-radius 0
    background-color #D32626
  &.current
    background-color #D32626

.item-complete
  margin 0
  height 48px
  border-top-left-radius 10%
  border-bottom-left-radius 10%
  background-color #D32626

@media screen and (max-width: 767px)
  .navegator
    & a
      font-size 1rem
  .item
    width 32px
    height 32px
    margin 10px
    margin-left 0
  .item-complete
    height 32px

@media screen and (min-width: 768px) and (max-width: 1280px)
  .navegator
    & a
      font-size 1.5rem
  .item
    width  48px
    height 48px
    margin 10px
    margin-left 0
  .item-complete
    height 48px
</style>
