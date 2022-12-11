<template>
  <footer class="footer">
    <div class="footer_left">
      <FooterLink :link-content="'github.png'" link-url="https://github.com/alinagizhdevan" link-type="img"
                  link-label="alinagizhdevan" new-tab/>
    </div>

    <div class="footer_right">
      <FooterLink :link-content="'\u00A9 Alina Gizhdevan'"/>
    </div>
  </footer>
</template>

<script>
import FooterLink from "@/components/footer/FooterLink";

export default {
  name: "Footer",
  components: {
    FooterLink,
  }
}
</script>

<style lang="scss" scoped>

.footer {
  margin: 10px 5px 0 5px;
  padding: 10px;
  border-top: 2px dashed white;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;

  &_left {
    margin-right: 10px;
  }

  &_right {
    display: flex;
    flex-direction: row;
    justify-content: flex-end;
    align-items: center;
  }
}

</style>