<template lang="html">
	<div class="friend">
		<img src="https://placehold.it/500x500" alt="">
		<div class="title">
			{{ friend.name.first }}&nbsp;{{ friend.name.last }}
		</div>
		<span class="indicator" v-bind:class="{'online': friend.online}"></span>
	</div>
</template>

<script>
export default {
	name: 'friend',
	props: ['friend'],
	data() {
		return {
			name: {
				first: 'First',
				last: 'Lastname'
			},
			online: true
		}
	}
}
</script>

<style scoped lang="scss">
.friend {
	display: flex;
	align-items: center;
	padding: 1rem;

	color: white;

	&:last-child {
		padding-bottom: 0;
	}

	img {
		display: inline;
		width: 3rem;
		height: 3rem;

		border-radius: 999px;
	}

	.title {
		flex-grow: 1;
		padding: 0 .4rem;

		display: inline;
		font-size: 1.5rem;
	}

	.indicator {
		min-width: 10px;
		min-height: 10px;

		background: #999;

		border-radius: 999px;

		&.online {
			background: #0f9;
		}
	}
}
</style>
