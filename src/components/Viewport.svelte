<script lang="ts">
	export let name: string = 'Wedington Photography'
</script>

<div id="viewport">
  {name}
</div>

<style lang="scss">
  @import '../styles/base';
  #viewport {
    @include viewport;
    @include flexCenterAll;
    flex-direction: column;
  }
</style>