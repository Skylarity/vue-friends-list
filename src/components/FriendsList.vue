<template>
	<div id="friendsList">
		<div class="search" v-bind:class="{'active': searchActive}">
			<icon name="search"></icon>
			<input id="searchBar" type="text" v-model="searchTerm" @focus="searchActive = true" @blur="searchActive = false">
		</div>
		<!-- TODO: loop through friends here -->
		<Friend v-for="friend in sortedFriends" v-bind:friend="friend"></Friend>
	</div>
</template>

<script>
import Friend from './Friend'

export default {
	name: 'friendsList',
	data() {
		return {
			searchActive: false,
			searchTerm: '',
			friends: [
				{
					name: {
						first: 'Channa',
						last: 'Chultz'
					},
					online: true
				},
				{
					name: {
						first: 'Kita',
						last: 'Schultz'
					},
					online: true
				},
				{
					name: {
						first: 'Chico',
						last: 'Dog'
					},
					online: false
				}
			]
		}
	},
	computed: {
		sortedFriends: function() {
			let sorted = []
			if (this.searchTerm.length > 0) {
				this.friends.forEach(friend => {
						const name = friend.name.first.toLowerCase() + ' ' + friend.name.last.toLowerCase()
						if (name.indexOf(this.searchTerm.toLowerCase()) > -1) {
							sorted.push(friend)
						}
				})
			} else {
				return this.friends
			}
			return sorted
		}
	},
	components: {
		Friend: Friend
	}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
#friendsList {
	margin: 0 auto;
	padding: 2rem;
	width: 33%;

	background: rgba(#444, .9);

	border-radius: 15px;

	.search {
		display: flex;
		align-items: center;

		padding: .25rem 1rem;
		margin-bottom: 15px;

		background: rgba(#fff, .2);

		border: none;
		border-radius: 999px;

		transition: .3s all;

		color: #fff;

		&.active {
			background: rgba(#fff, .9);
			outline: none;
			color: #444;
		}

		input[type=text] {
			flex-grow: 1;
			padding-left: .5rem;

			color: inherit;

			font-family: inherit;
			font-size: 1.25rem;

			background: transparent;
			border: none;

			&:focus, &:active {
				outline: none;
			}
		}
	}
}
</style>
