<script>
	// @ts-nocheck
	import { onMount } from 'svelte';
	import '@kyndryl-design-system/shidoka-foundation/scss/root.scss';
	import '@kyndryl-design-system/shidoka-foundation/scss/utility/typography.scss';
	import '@kyndryl-design-system/shidoka-foundation/scss/utility/grid.scss';
	import '../app.css';
	import UserAvatar from '@kyndryl-design-system/shidoka-icons/svg/monochrome/16/user.svg?raw';
	import CircleStroke from '@kyndryl-design-system/shidoka-icons/svg/monochrome/16/circle-stroke.svg?raw';

	let mounted = false;
	onMount(async () => {
		await import('@kyndryl-design-system/shidoka-applications/components/global/uiShell');
		await import('@kyndryl-design-system/shidoka-applications/components/global/header');
		await import('@kyndryl-design-system/shidoka-applications/components/global/localNav');
		await import('@kyndryl-design-system/shidoka-applications/components/global/footer');
		mounted = true;
	});
</script>

{#key mounted}
	<kyn-ui-shell>
		<kyn-header divider="" apptitle="Shidoka SvelteKit">
			<kyn-header-nav>
				<kyn-header-link href="javascript:void(0)">{@html CircleStroke}Link 1 </kyn-header-link>
				<kyn-header-link href="javascript:void(0)" isActive>{@html CircleStroke}Link 2 </kyn-header-link>
				<kyn-header-link href="javascript:void(0)">{@html CircleStroke}
					Link 3

					<kyn-header-link slot="links" href="javascript:void(0)"> Sub Link # 1 </kyn-header-link>
					<kyn-header-link slot="links" href="javascript:void(0)"> Sub Link 2 </kyn-header-link>
				</kyn-header-link>
			</kyn-header-nav>

			<kyn-header-flyouts>
				<kyn-header-flyout label="Menu">
					<span slot="button">{@html UserAvatar}</span>
					
						<kyn-header-link href="javascript:void(0)"> Login </kyn-header-link>
						<kyn-header-link href="javascript:void(0)"> Sign up </kyn-header-link>
				</kyn-header-flyout>

				<kyn-header-flyout assistiveText="My Account" hideArrow>
					<kyn-header-avatar initials="KB" slot="button" />

					<kyn-header-link href="javascript:void(0)"> Logout </kyn-header-link>
				</kyn-header-flyout>
			</kyn-header-flyouts>
		</kyn-header>

		<kyn-local-nav>
			<kyn-local-nav-link href="javascript:void(0)" active="">
				<span slot="icon" class="iconStyle">{@html UserAvatar}</span>
				Link 1
			</kyn-local-nav-link>

			<kyn-local-nav-link href="javascript:void(0)">
				<span slot="icon" class="iconStyle">{@html UserAvatar}</span>
				Link 2

				<kyn-local-nav-link slot="links" href="javascript:void(0)"> L2 Link 1 </kyn-local-nav-link>
				<kyn-local-nav-link slot="links" href="javascript:void(0)"> L2 Link 2 </kyn-local-nav-link>
			</kyn-local-nav-link>

			<kyn-local-nav-link href="javascript:void(0)" expanded="">
				<span slot="icon" class="iconStyle">{@html UserAvatar}</span>
				Link 3

				<kyn-local-nav-link slot="links" href="javascript:void(0)">
					L2 Link 1

					<kyn-local-nav-link slot="links" href="javascript:void(0)">
						L3 Link 1
					</kyn-local-nav-link>
					<kyn-local-nav-link slot="links" href="javascript:void(0)">
						L3 Link 2
					</kyn-local-nav-link>
				</kyn-local-nav-link>
			</kyn-local-nav-link>
		</kyn-local-nav>

		<main><slot /></main>

		<kyn-footer>
			<span slot="copyright"> Copyright &copy; 2025 Kyndryl Inc. All rights reserved. </span>
		</kyn-footer>
	</kyn-ui-shell>
{/key}

<style lang="scss">
	@use '@kyndryl-design-system/shidoka-foundation/scss/mixins/typography.scss';
</style>
