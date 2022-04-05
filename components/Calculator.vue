<template>
  <div class="space">
    <div class="calc">
      <header>
        <span>calc</span>
        <div class="theme">THEME</div>
      </header>
      <main>{{ screen }}</main>
      <section>
        <button v-bind:key="key" @click="press(key)" v-for="key of keys">
          {{ key }}
        </button>
      </section>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    press: function (key) {
      console.log(key, typeof this.screen);

      if (this.finished && !isNaN(key)) {
        this.screen = "";
      }

      if (key == "del") {
        this.screen = this.screen.slice(0, -1);
        this.finished = false;
        return;
      }
      if (key == "reset") {
        this.screen = "";
        return;
      }

      if (key == "=") {
        this.screen = this.screen.replaceAll("×", "*");
        this.screen = eval(this.screen).toString();
        this.finished = true;
        return;
      }

      this.screen += key;
      this.finished = false;
    },
  },
  data() {
    return {
      finished: false,
      screen: "",
      keys: [
        7,
        8,
        9,
        "del",
        4,
        5,
        6,
        "+",
        1,
        2,
        3,
        "-",
        ".",
        0,
        "/",
        "×",
        "reset",
        "=",
      ],
    };
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Spartan:wght@100;200;300;400;500;600;700;800;900&display=swap");

:root {
  --primary-color: hsl(222, 26%, 31%);
  --secondary-color: hsl(224, 36%, 15%);
  --tertiary-color: hsl(223, 31%, 20%);
  --text-color: #ffffff;
  --button-primary: hsl(30, 25%, 89%);
}
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  height: 100%;
  width: 100%;
}
.space {
  height: 100%;
  width: 100%;
  background-color: var(--primary-color);
  display: flex;
  align-items: center;
  justify-content: center;
}

.calc {
  display: flex;
  flex-direction: column;
  height: 50%;
  color: var(--text-color);
  gap: 1rem;
  font-weight: 700;
  max-width: 440px;
  margin: 2rem;
}

header {
  display: flex;
  justify-content: space-between;
  font-family: Spartan;
  height: 2rem;
}

header > span {
  font-size: 1.5rem;
}

.theme {
  display: none;
}

main {
  background-color: var(--secondary-color);
  border-radius: 0.5rem;
  display: flex;
  justify-content: flex-end;
  align-items: center;
  padding: 0 1.5rem;
  font-size: 2.5rem;
  height: 12rem;
}

section {
  background-color: var(--tertiary-color);
  border-radius: 0.5rem;
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-template-rows: repeat(5, 1fr);
  gap: 1rem 1rem;
  padding: 1rem;
}

button {
  font-size: 1.5rem;
  text-transform: uppercase;
  background-color: hsl(30, 25%, 89%);
  color: var(--primary-color);
  font-weight: 700;
  border-radius: 0.5rem;
}

button:nth-child(4),
button:nth-child(17) {
  background-color: hsl(225, 21%, 49%);
  color: white;
  font-size: 1rem;
}

button:nth-last-child(1) {
  grid-column-start: 3;
  grid-column-end: 5;
  color: white;
  background-color: hsl(6, 63%, 50%);
}

button:nth-last-child(2) {
  grid-column-start: 1;
  grid-column-end: 3;
}
</style>
