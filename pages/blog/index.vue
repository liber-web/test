<template>
  <section id="blog" v-cloak>
			<div class="container">
				<div class="teko subTitle">STAFF BLOG</div>
				<h2>スタッフブログ</h2>
				<p class="blog-head">湘南の暮らし情報をお届けします</p>
				<v-row>
					<v-col									
						cols="6"
						md="3"							
						class="blog"
						v-for="post in users" :key="post.id"	
					>
						<v-card
							class="blog-box"
							flat	
							:href="post.link"																									
							>
																				
						
							<div class="blog-box-bm">
								<h3>{{post.title}}</h3>
								<hr>
								<div class="blog-box-bm-txt" v-html="post.content"></div>
								<span class="triangle"></span>
							</div>
						</v-card>
					</v-col>
				</v-row>
				<a href="blog" class="btn">ブログ一覧へ<i class="fas fa-chevron-right"></i></a>
			</div>
		</section>
  
 
</template>

<script>
const axios = require('axios')
let url = 'https://liber.liber-develop.com/wp-json/wp/v2/posts/?per_page=3'

export default {
 
  async asyncData({ params, error, payload }) {
    if (payload) {     
      return { users: payload }
    }else{
       return axios.get(url).then((res) => {
        return { users: res.data }
      })
    }
  }
}
 
</script>