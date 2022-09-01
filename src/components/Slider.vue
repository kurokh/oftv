<template>
	<section class="wrap" :class="{'loaded' : loaded}">
		<div class="category">
			<a :href="category.link" target="_blank" class="category_title">{{category.title}}</a>
			<div class="category_videos">
				<div class="video_item" v-for="video in category.videos">
					<a :href="video.link" target="_blank" class="video_wrap">
						<div class="video_thumb">
							<v-lazy-image 
								:src="video.thumb"
								:src-placeholder="video.thumb_preload" 
							/>
						</div>
						<div class="video_bottom">
							<div class="video_title">{{video.title}}</div>
							<div class="video_creator" @click="handleCategoryClick(category.link)">{{video.creator}}</div>
						</div>
					</a>
				</div>
			</div>
		</div>
	</section>
</template>
<script>
	import VLazyImage from "v-lazy-image"
	export default{
		components:{
			VLazyImage
		},
		data(){
			return{
				category:{
					link: 'https://of.tv/creators/in-real-life',
					title: 'In Real Life',
					videos: [
						{
							thumb: '/img/thumb1.jpg',
							thumb_preload: '/img/thumb1-min.jpg',
							title: 'In Real Life with Nata Gata',
							creator: 'In Real Life',
							link: 'https://of.tv/video/62d5c8b0c926fc00012a2a40'
						},
						{
							thumb: '/img/thumb2.jpg',
							thumb_preload: '/img/thumb2-min.jpg',
							title: 'In Real Life with Angie & Maria',
							creator: 'In Real Life',
							link: 'https://of.tv/video/62ec1a789655e20001dbd4ae'
						},
						{
							thumb: '/img/thumb3.jpg',
							thumb_preload: '/img/thumb3-min.jpg',
							title: 'In Real Life with Bruna Lima',
							creator: 'In Real Life',
							link: 'https://of.tv/video/62d5c8b0c926fc00012a2a40'
						}
					],
				},
				loaded: false
			}
		},
		methods: {
			handleCategoryClick(url){
				window.open(url, '_blank');
			}
		},
		mounted(){
			setTimeout(() => this.loaded = true, 300)
		}
	}
</script>