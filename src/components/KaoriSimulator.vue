<template>
  <div>
    <img
      src="https://cdn.discordapp.com/avatars/745950401441955893/67ec3fe9b61b7d52d77fab7ec7b57cd2.webp"
      alt="Kaori's Discord PFP"
    />

    <h1>Kaori Simulator</h1>
    <blockquote>
      {{ joke }}
      <span>- Local Glorified Seagull</span>
    </blockquote>
    <button role="button" @click="fetchJoke">Click Me!</button>

    <h3>Jokes Survived: {{ clicks }}</h3>
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";
import ky from "ky";

const joke = ref("Click the Button to get started.");
const clicks = ref(0);

async function fetchJoke() {
  joke.value = await ky
    .get("https://icanhazdadjoke.com", {
      headers: {
        Accept: "text/plain",
      },
    })
    .text();

  clicks.value++;
}
</script>

<style lang="scss" scoped>
@import url(https://fonts.googleapis.com/css?family=Open+Sans:400italic);
blockquote {
  font-size: 1.4em;
  width: 60%;
  margin: 50px auto;
  font-family: Open Sans;
  font-style: italic;
  color: #555555;
  padding: 1.2em 30px 1.2em 75px;
  border-left: 8px solid #78c0a8;
  line-height: 1.6;
  position: relative;
  background: #ededed;

  &::before {
    font-family: Arial;
    content: "\201C";
    color: #78c0a8;
    font-size: 4em;
    position: absolute;
    left: 10px;
    top: -10px;
  }

  &::after {
    content: "";
  }

  span {
    display: block;
    color: #333333;
    font-style: normal;
    font-weight: bold;
    margin-top: 1em;
  }
}

img {
  border-radius: 50%;
  border: #faa61a 5px solid;
}

button {
  align-items: center;
  appearance: none;
  background-image: radial-gradient(
    100% 100% at 100% 0,
    #5adaff 0,
    #5468ff 100%
  );
  border: 0;
  border-radius: 6px;
  box-shadow: rgba(45, 35, 66, 0.4) 0 2px 4px,
    rgba(45, 35, 66, 0.3) 0 7px 13px -3px, rgba(58, 65, 111, 0.5) 0 -3px 0 inset;
  box-sizing: border-box;
  color: #fff;
  cursor: pointer;
  display: inline-flex;
  font-family: "JetBrains Mono", monospace;
  height: 48px;
  justify-content: center;
  line-height: 1;
  list-style: none;
  overflow: hidden;
  padding-left: 16px;
  padding-right: 16px;
  position: relative;
  text-align: left;
  text-decoration: none;
  transition: box-shadow 0.15s, transform 0.15s;
  user-select: none;
  -webkit-user-select: none;
  touch-action: manipulation;
  white-space: nowrap;
  will-change: box-shadow, transform;
  font-size: 18px;
  &:focus {
    box-shadow: #3c4fe0 0 0 0 1.5px inset, rgba(45, 35, 66, 0.4) 0 2px 4px,
      rgba(45, 35, 66, 0.3) 0 7px 13px -3px, #3c4fe0 0 -3px 0 inset;
  }

  &:hover {
    box-shadow: rgba(45, 35, 66, 0.4) 0 4px 8px,
      rgba(45, 35, 66, 0.3) 0 7px 13px -3px, #3c4fe0 0 -3px 0 inset;
    transform: translateY(-2px);
  }

  &:active {
    box-shadow: #3c4fe0 0 3px 7px inset;
    transform: translateY(2px);
  }
}
</style>