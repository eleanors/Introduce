<template>
	<div v-if="toastShow" class="music-tips-cover">
		<div class="alert">
			<div class="tipcon">{{toastContent}}</div>
			<div class="ok" @click="isHide">OK</div>
		</div>
	</div>
</template>
<script>
	import {setToastShow, setToastContent} from '../vuex/actions';
	export default {
			name: 'Toast',
			methods : {
					isHide : function() {
							this.setToastShow(false);
							this.setToastContent('');
					}
			},
			vuex : {
					actions : {
							setToastShow : setToastShow,
							setToastContent : setToastContent
					},
					getters : {
							toastShow : state => state.toastShow,
							toastContent : state => state.toastContent
					}
			}
	}
</script>
<style lang="scss">
	.music-tips-cover {
		    position: fixed;
		    width: 100%;
		    height: 100%;
		    top: 0;
		    left: 0;
		    z-index: 10000;
		    background: rgba(0,0,0,.6);
    		-webkit-transition: opacity 3.2s linear;
    		transition: opacity 3.2s linear;
		    .alert {
		    	position: fixed;
			    z-index: 5000;
			    width: 85%;
			    top: 50%;
			    left: 50%;
			    -webkit-transform: translate(-50%,-50%);
			    transform: translate(-50%,-50%);
			    background-color: #fafafc;
			    text-align: center;
			    border-radius: 3px;
			    overflow: hidden;
			    transition-property: transform,opacity,-webkit-transform!important;
			    .tipcon {
			    	padding: 20px 20px;
				    font-size: 15px;
				    color: #888;
			    }
			    .ok {
				    position: relative;
				    line-height: 42px;
				    margin-top: 20px;
					color: #0bb20c;
				    font-size: 17px;
				    text-align: center;
			    }
		    }
		    .alert-transition {
		    	opacity: 1;
				webkit-transition-duration: .4s;
    			transition-duration: .4s;
		    }
	}
	.tips-leave {
		opacity : 0;
	}
</style>