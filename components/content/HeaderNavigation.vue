<template>
<nav id="nav" class="header-navigation" :class="{ 'header-navigation__is-pinned': isPinned }">
		<div class="header-navigation-container">
			<template v-for="(text, index) in navigation" :key="text">
				<button @click="scrollToElement(index)">
					{{ text }}
				</button>
			</template>
		</div>
	</nav>
</template>

<script setup lang="ts">
defineProps<{ navigation: String[]; }>()
const isPinned = ref<boolean>(false)

const scrollElementOne = ref<HTMLElement | null>(null);
const scrollElementTwo = ref<HTMLElement | null>(null);
const scrollElementThird = ref<HTMLElement | null>(null);
onMounted(() => {
	scrollElementOne.value = document?.getElementById('scroll-1')
	scrollElementTwo.value = document?.getElementById('scroll-3')
	scrollElementThird.value = document?.getElementById('scroll-2')

	window.addEventListener('scroll', checkSticky);
	checkSticky();
})

onUnmounted(() => {
	window.removeEventListener('scroll', checkSticky);

})

const scrollToElement = (index: number) => {
	const HtmlElement = [scrollElementOne, scrollElementTwo, scrollElementThird]
	if (HtmlElement[index]) {
		HtmlElement[index].value?.scrollIntoView({ behavior: 'smooth', })
	}
}

const checkSticky = () => {
	const element = document?.getElementById('nav')
	const rect = element?.getBoundingClientRect();

	if (!rect) { return }
	if (isPinned.value !== rect!.top <= 1) {
		isPinned.value = rect!.top <= 1;
	}
}

</script>


<style lang="scss" scoped>
.header {
	&-navigation {
		border: 1px solid #04BE7B;
		border-radius: 6px;
		width: fit-content;
		margin: auto;
		margin-bottom: 42px;
		display: flex;
		width: 100%;
		max-width: 50vw;

		button {
			width: 100%;
			font-size: 20px;
			font-weight: 600;
			color: #04BE7B;
			text-align: center;
			padding: 10px 22px;
			background: transparent;
			border-radius: 6px;
		}

		:nth-child(2) {
			width: 120%;
			background: #04BE7B;
			color: #FFF;
		}

		&-container {
			max-height: 41px;
			display: flex;
			width: calc(100% - 40px);
			text-align: center;
			border: none;
			border-radius: 0;
			margin-left: auto;
			margin-right: auto;
		}
	}

	@media (max-width: 1024px) {

		&-navigation {
			max-width: inherit;
			margin-bottom: 21px;

			button {
				font-size: 11px;
				padding: 10px 5px;
			}
		}
	}

	@media (max-width: 500px) {
		&-navigation {
			position: sticky;
			top: 0px;
			background: white;
			width: 100vw;
			margin-left: -20px;
			border: none;
			border-radius: 0;
			overflow-anchor: none;

			&__is-pinned {
				box-shadow: 0px 3px 9px 0px rgba(134, 134, 134, 0.76);
			}

			&-container {
				max-height: inherit;
				display: flex;
				width: calc(100% - 40px);
				text-align: center;
				border: 1px solid #04BE7B;
				border-radius: 6px;
				margin: 10px auto;
			}

			button {
				font-size: 14px;
			}
		}
	}
}
</style>