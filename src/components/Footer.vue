<template>
  <footer>
    <div>
      by @raflidev
    </div>
    <div>
      <a class="text-white" href="http://instagram.com/raflidev">
        <u>
          ig
        </u>
      </a>
      /
      <a class="text-white" href="http://twitter.com/raflidev">
        <u>tw</u>
      </a>
      /
      <a class="text-white" href="http://github.com/raflidev">
        <u>ghub</u>
      </a>
    </div>
  </footer>
</template>

<script>
export default {};
</script>

<style>
footer {
  display: flex !important;
  justify-content: space-between;
  align-items: center;
  position: fixed;
  bottom: 0px;
  left: 0px;
  transform: translate(-50%);
  margin-left: 50%;
  padding: 8px 5%;
  background: #2a343e;
  width: 100%;
  max-width: 428px;
}
</style>
