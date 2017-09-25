<template>
	<div>
		<label>Api twitch</label>
		<form v-on:submit="getStream" id="form-twitch">
			<input id="username" type="text" v-model="user">
			<button type="submit">Envoyez</button>
		</form>
        <div class="card">
                <img :src="infos.preview.large"/>      
        <div class="card-content">
            <div class="media">
            <div class="media-left">
                <figure class="image is-48x48">
                <img :src="infos.channel.logo">
                </figure>
            </div>
            <div class="media-content">
                <p class="title is-4">{{infos.channel.display_name}}</p>
                <p class="subtitle is-6">{{infos.game}}</p>
                <p class="subtitle is-6">{{infos.channel.status}}</p>
                <p class="subtitle is-6">{{infos.viewers}}</p>
            </div>
            </div>

            <div class="content">
            <a></a>.
            <a href="#"></a> <a href="#"></a>
            <br>
            <span>{{infos.channel.updated_at}}</span>
            </div>
        </div>
        </div>
            </div>
        
</template>

<script>
	import axios from 'axios'
	
	export default {
		data(){
			return {
				apiKey: 'API KEY',
				user:'',
                stream:null,
                infos: ""
			}
		},
		methods:{
			test: function(e){
				e.preventDefault()
				console.log('yeah')
			},
			getStream: function(e){
				e.preventDefault()
				console.log(this.user)
				let stream = axios.get(`https://api.twitch.tv/kraken/streams/${this.user}?client_id=${this.apiKey}`)
                    .then(res =>  this.infos = res.data.stream)
					.catch(function(err){
						console.log(err)
					})
				stream.then(res => this.stream = res)
			}
		}
	}
</script>% 

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>