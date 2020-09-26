<template>
  <div id="nav">
    <router-link to="/">Home</router-link> |
    <router-link to="/about">About</router-link>
  </div>
  <router-view/>
</template>

<style lang="scss">
body {
  margin:0 !important;
  padding:0 !important;

}

.flex {
  display:flex;
}
</style>
