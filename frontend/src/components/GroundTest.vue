<template>
  <div class="GroundTest">
      <HeaderTest/>
      <MemoTest/>
      <FooterTest/>
  </div>
</template>

<script>

import FooterTest from "./FooterTest.vue";
import HeaderTest from "./HeaderTest.vue";
import MemoTest from "./MemoTest.vue";
export default {
  components:{ HeaderTest, FooterTest, MemoTest}
}
</script>
