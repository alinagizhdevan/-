<template>
  <a v-if="linkUrl" :href="`${linkUrl}`" class="footer_text footer_link" :target="(newTab) ? '_blank' : false">
    <img v-if="linkType === 'img'" :src="getImgUrl(linkContent)" :alt="linkContent" class="footer_logo">
    <span v-else>{{ linkContent }}</span>
    <span v-if="linkType === 'img' && linkLabel">{{ linkLabel }}</span>
  </a>
  <span v-else class="footer_text">{{ linkContent }}</span>
</template>

<script>
export default {
  name: "FooterLink",
  props: {
    linkUrl: String,
    linkContent: String,
    linkType: String,
    linkLabel: String,
    newTab: Boolean,
  },
  methods: {
    getImgUrl(pic) {
      return require('@/assets/' + pic)
    }
  }
}
</script>

<style lang="scss" scoped>

.footer {
  &_text {
    margin-top: 8px;
    display: flex;
    justify-content: center;
    align-items: center;
    color: #a9a9a9;
    text-decoration: none;
  }

  &_link {
    font-size: 1.1em;

    &:hover {
      color: #fff;
      text-decoration: none;
    }
  }

  &_logo {
    width: 1em;
    margin-right: 8px;
  }
}

</style>