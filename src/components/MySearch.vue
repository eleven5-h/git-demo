<template>
  <section class="jumbotron">
		<h3 class="jumbotron-heading">Search Github Users</h3>
		<div>
			<input type="text" placeholder="enter the name you search" v-model="keyWord"/>&nbsp;
			<button @click="searchUsers">Search</button>
		</div>
	</section>
</template>

<script>
import axios from 'axios'
export default {
    name:'MySearch',
    data(){
        return {
            keyWord:''
        }
    },
    methods:{
        searchUsers(){
            this.$bus.$emit('UserList',{isFirst:false,isLoading:true,Users:[],errorMsg:''})
            axios.get(`https://api.github.com/search/users?q=${this.keyWord}`).then(
                response => {
                    this.$bus.$emit('UserList',{isLoading:false,Users:response.data.items,errorMsg:''})
                },
                error => {
                    this.$bus.$emit('UserList',{isLoading:false,Users:[],errorMsg:error.message})
                }
            )
        }
    }
}
</script>

<style>

</style>