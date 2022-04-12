<template>
  <div :style="animation" id='oioi' class="nav" v-bind:class="{ open: isOpen, closed: (!isOpen || isOpen == '' )}">
    <ul :style="animation" v-bind:class="{ closedtxt: !isOpen, opentxt: isOpen }">
      <li v-bind:key="name" v-for="{ name, path } of items">
        <nuxt-link :to="path">{{ name.toUpperCase() }}</nuxt-link>
      </li>
    </ul>
    <button class="openNav" @click="openNav">
      {{ isOpen ? "Close" : "Open" }}
    </button>
  </div>
</template>

<script>
export default {
  created() {
    this.$router.options.routes.forEach((route) => {
      this.items.push({
        name: route.name,
        path: route.path,
      });
    });
    this.items = this.items.sort(function (a, b) {
      if (a.name == "index") return -1;
      if (b.name == "index") return 1;
      if (a.name > b.name) {
        return 1;
      }
      if (a.name < b.name) {
        return -1;
      }
      return 0;
    });
    setTimeout(() => this.isOpen = false, 250);
  },
  data() {
    return {
      items: [],
      isOpen :'',
    };
  },
  methods: {
    openNav: function () {
        console.log(this.isOpen)
      this.isOpen = !this.isOpen;
    },
  },
  computed:{
      animation(){
          return{
                "animation-duration": this.isOpen !== ''? "250ms":"0ms"

          }
      }
  }
};
</script>

<style scoped>
.openNav {
  /* background-color: white; */
  margin-left: auto;
}

.nav {
  --nav-color: yellow;
  display: flex;
  justify-content: space-between;
  width: 100%;
  padding: 0 1rem;
}

.nav ul {
  display: flex;
  gap: 1rem;
}
.closed {
  animation-name: close;
  position: fixed;
  background: none;
}

.open {
  background-color: var(--nav-color);
  animation-name: open;
  /* transition: ease-in-out 200ms; */
}

.closedtxt {
  position: fixed;
  animation-name: closeText;
  top: -24px;
}

.opentxt {
  position: fixed;
  animation-name: openText;
}

@keyframes open {
  from {
    height: 0px;
  }
  to {
    height: 24px;
  }
}
@keyframes close {
  from {
    background-color: var(--nav-color);
    height: 24px;
    position: inherit;
  }
  to {
    background-color: var(--nav-color);
    height: 0px;
    position: inherit;
  }
}
@keyframes openText {
  from {
    top: -24px;
  }
  to {
    top: 0px;
  }
}

@keyframes closeText {
  from {
    top: 0px;
  }
  to {
    top: -24px;
  }
}
</style>
