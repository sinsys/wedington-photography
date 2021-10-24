<script lang="ts">
  import Viewport from './components/Viewport.svelte'
</script>

<main>
  <Viewport />
</main>

<style lang="scss">
  @import './styles/base';
  main {
    @include page;
    @include fontWorkSans;
    color: $light;
  }
</style>