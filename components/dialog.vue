<template>
	<div>
		<div class="dialog-wrap" v-if="isShow" @click.stop="aboutClose">
			<div class="dialog-cover" @click.stop="">
				<div class="dialog-content">
				<p class="dialog-close" @click.stop="aboutClose">X</p>
			        <slot></slot>
			    </div>
			</div>
		</div>
	</div>
</template>

<script>
export default {
  props:{
  	isShow:{
  		type:Boolean,
  		default:false
  	}
  },
  methods:{
  	aboutClose () {
       this.$emit("closeAbout")
  	}
  }
}
</script>

<style>
	.dialog-wrap{
		position:fixed;width:100%;height:100%;
		;top:0;left:0;background: rgba(0,0,0,.5); -moz-opacity: 0.5;filter: alpha(opacity=50);/*IE兼容透明度的写法*/z-index:11;
	}
	.dialog-cover{
		position:absolute;left:50%;
	    width:500px;height:auto;margin-left:-150px;background:#fff;border:2px solid #000;top:50%;margin-top:-50px;
	}
	.dialog-content{
		width:100%;height:auto;padding:15px;
		color:#000;line-height:30px;
	}
	.dialog-close{
		position:absolute;top:0;right:0;
		width:30px;height:30px;text-align: center;line-height:30px;cursor: pointer;
	}

</style>