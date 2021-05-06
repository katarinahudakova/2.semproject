<template>
  <footer class="footer font-small text-center">
    
    <ul class="list-inline">
      <li
        v-for="(item, i) in social"
        :key="i"
        class="social-item list-inline-item"
      >
        <a :href="item.url" :alt="item.name">
          <i :class="item.faClass"> </i>
        </a>
      </li>
    </ul>

    <div class="copyright">
      <p>
        Copyright © {{ new Date().getFullYear() }}
        {{ text.main.name.first }} {{ text.main.name.last  }}.
        {{ text.footer.copyrightText }}
      </p>
    </div>
    
  </footer>
</template>

<script>
import data from "../../data/data.json";

export default {
  name: "Footer",
  components: {},
  props: {},
  data() {
    return {
      text: data,
      social: data.contact.social,
    };
  },
};
</script>

<style lang="scss"></style>
