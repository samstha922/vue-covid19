<template>
<div>
    {{ msg }}
	<b-nav>
		<b-nav-item disabled>Fancy Quiz App</b-nav-item>
		<b-nav-item disabled>Counter</b-nav-item>
	</b-nav>
	<hr>
</div>
</template>

<script>
	export default{
        name:'Header',
        props: [
            'msg'
        ]
	}
</script>