<template>
<div class="ctn">
  <button class="btn" @click="randomize">Randomize</button>
</div>
</template>

<script>
export default {
setup(props, {emit})
{
    const randomize = (() => {
		emit('randomizer')
	})

    return {randomize}
}
}
</script>

<style>
.btn{
    background-color:blue;
    color: white;
    width:100%;
    bottom: 0;
    position:fixed;
    left:0;
    height:50px;
}
</style>