<script>
	// @ts-nocheck
	import { onMount } from 'svelte';
	import '@kyndryl-design-system/shidoka-foundation/scss/root.scss';
	import '@kyndryl-design-system/shidoka-foundation/scss/utility/typography.scss';
	import '@kyndryl-design-system/shidoka-foundation/scss/utility/grid.scss';
	import '../app.css';
	import switcherIcon from '@kyndryl-design-system/shidoka-foundation/assets/svg/switcher.svg?raw';
	import UserAvatar from 'carbon-icons-svelte/lib/UserAvatar.svelte';

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
			<kyn-header-panel slot="left" heading="Panel Heading">
				<span slot="button">
					{@html switcherIcon}
				</span>

				<kyn-header-panel-link href="javascript:void(0)">
					<UserAvatar size={24} />
					Link 1
				</kyn-header-panel-link>
				<kyn-header-panel-link href="javascript:void(0)">
					<UserAvatar size={24} />
					Link 2
				</kyn-header-panel-link>
				<kyn-header-panel-link href="javascript:void(0)">
					<UserAvatar size={24} />
					Link 3
				</kyn-header-panel-link>
			</kyn-header-panel>

			<kyn-header-nav>
				<kyn-header-link href="javascript:void(0)"> Link 1 </kyn-header-link>
				<kyn-header-link href="javascript:void(0)" isActive> Link 2 </kyn-header-link>
				<kyn-header-link href="javascript:void(0)">
					Link 3

					<kyn-header-link slot="links" href="javascript:void(0)"> Sub Link # 1 </kyn-header-link>
					<kyn-header-link slot="links" href="javascript:void(0)"> Sub Link 2 </kyn-header-link>
				</kyn-header-link>
			</kyn-header-nav>

			<kyn-header-flyouts>
				<kyn-header-flyout>
					<span slot="button">Sign in</span>

					<div>
						<kyn-header-link href="javascript:void(0)"> Login </kyn-header-link>
						<kyn-header-link href="javascript:void(0)"> Sign up </kyn-header-link>
					</div>
				</kyn-header-flyout>

				<kyn-header-flyout assistiveText="My Account" hideArrow>
					<kyn-header-avatar initials="KB" slot="button" />

					<kyn-header-link href="javascript:void(0)"> Logout </kyn-header-link>
				</kyn-header-flyout>
			</kyn-header-flyouts>
		</kyn-header>

		<kyn-local-nav>
			<kyn-local-nav-link href="javascript:void(0)" active="">
				<UserAvatar size={20} slot="icon" />
				Link 1
			</kyn-local-nav-link>

			<kyn-local-nav-link href="javascript:void(0)">
				<UserAvatar size={20} slot="icon" />
				Link 2

				<kyn-local-nav-link slot="links" href="javascript:void(0)"> L2 Link 1 </kyn-local-nav-link>
				<kyn-local-nav-link slot="links" href="javascript:void(0)"> L2 Link 2 </kyn-local-nav-link>
			</kyn-local-nav-link>

			<kyn-local-nav-link href="javascript:void(0)" expanded="">
				<UserAvatar size={20} slot="icon" />
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
			<span slot="copyright"> Copyright &copy; 2023 Kyndryl Inc. All rights reserved. </span>
		</kyn-footer>
	</kyn-ui-shell>
{/key}

<style lang="scss">
	@use '@kyndryl-design-system/shidoka-foundation/scss/mixins/typography.scss';
</style>
