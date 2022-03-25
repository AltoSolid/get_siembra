<template>
  <div class="col-md-3">
    <div class="panel panel-default">
      <div class="panel-body quote">
        <slot />
      </div>
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style>
.panel-body {
  font-family: "Franklin Gothic Medium", "Arial Narrow", Arial, sans-serif;
  font-size: 12px;
  color: #6e6e6e;
}

.quote {
  cursor: pointer;
}

.quote:hover {
  background-color: greenyellow;
}
</style>
