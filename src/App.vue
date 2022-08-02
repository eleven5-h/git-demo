<template>
  <div class="container">
		<my-search/>
        <my-list/>
	</div>
</template>

<script>
import MySearch from './components/MySearch'
import MyList from './components/MyList'

export default {
  name: 'App',
  components: {
    MySearch,
    MyList
  }
}
</script>

<style>

</style>
