<template>
  <div class="nav" v-bind:class="{ open: isOpen, closed: !isOpen }">
    <ul v-if="isOpen">
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
      console.log(route);
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
  },
  data() {
    return {
      items: [],
      isOpen: false,
    };
  },
  methods: {
    openNav: function () {
      this.isOpen = !this.isOpen;
    },
  },
};
</script>

<style scoped>
.openNav {
  /* background-color: white; */
  margin-left: auto;
}
.nav {
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
  animation-duration: 500ms;
  position: fixed;
  background: none;
}

.open {
  background-color: lightgray;
  animation-name: open;
  animation-duration: 500ms;
  /* transition: ease-in-out 200ms; */
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
    height: 24px;
    position: inherit;
  }
  to {
    height: 0px;
    position: inherit;
  }
}
</style>
