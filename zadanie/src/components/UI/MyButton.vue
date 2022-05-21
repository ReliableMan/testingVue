<template>
  <button class="btn">
    <slot></slot>
  </button>
</template>

<script>
export default {
  name: "my-button"
}
</script>

<style scoped>
.btn{
  width: 140px;
  height: 35px;
  border-radius: 15px;
  margin-top: 15px;
  align-self: flex-start;
  padding: 4px 8px;
  background: linear-gradient(-45deg, #655396, #cebabf, #68a2b1, #23d541);
	background-size: 400% 400%;
	animation: animate_gradient 4.5s ease infinite;
}
.butn:hover {
	animation: none;
}
@keyframes animate_gradient {
	0% {
		background-position: 0% 50%;
	}
	50% {
		background-position: 100% 50%;
	}
	100% {
		background-position: 0% 50%;
	}
}
</style>
