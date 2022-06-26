<template>
  <div id="nav">
    <router-link to="/" id="logo_url">
      <img :src="logo" :alt="msgAlt" />
    </router-link>
    <router-link to="/"> Home </router-link>
    <router-link to="/pedidos"> Pedidos </router-link>
  </div>
</template>

<script>
export default {
  name: "Navbar",
  props: ["logo", "msgAlt"],
};
</script>

<style scoped>
#nav {
  background-color: #222;
  border-bottom: 4px solid #111;
  padding: 1rem 3.5rem;
  display: flex;
  justify-content: flex-end;
  align-items: center;
}

#nav #logo_url {
  margin: auto;
  margin-left: 0;
}

#nav #logo_url img {
  width: 40px;
  height: 40px;
}

#nav a {
  color: #fcba03;
  text-decoration: none;
  margin: 0.9rem;
  transition: 0.5s;
}

#nav a:hover {
  color: #fff;
}
</style>