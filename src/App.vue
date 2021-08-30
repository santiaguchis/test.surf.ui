<template>
	<Title/>
	<SurfIndex/>
</template>
<script>

import Title from './components/Title.vue'
import SurfIndex from './views/Surf/Index.vue'
export default {
	name: 'App',
	components: {
		Title,
		SurfIndex
	}
}
</script>