<script lang="ts">
	import { uniqueId } from '../utils/uniqueId'
	import IconCheck from 'virtual:icons/heroicons-outline/check'

	export let checked = false

	const id = `checkbox-${uniqueId()}`
</script>

<div class="checkbox">
	<input type="checkbox" bind:checked on:change {id} name={id} />
	<label for={id} class="checkbox__label">
		<span class="checkbox__label__box">
			<IconCheck />
		</span>
		<slot />
	</label>
</div>

<style lang="postcss">
	.checkbox {
		input {
			display: none;
		}

		display: inline-flex;
		align-items: center;
		grid-gap: 0.5rem;

		&__label {
			display: flex;
			align-items: center;
			grid-gap: 0.5rem;

			> :global(.icon) {
				/* Icon on checkbox helps to be a little larger than normal icons 16px -> 18px */
				width: 18px;
				margin-right: -2px;
			}

			&__box {
				height: 1rem;
				width: 1rem;
				display: flex;
				border-radius: 0.25rem;
				background-color: var(--color-button-bg);
				justify-content: center;
				align-items: center;

				> :global(.icon) {
					display: none;
					width: 1rem;
					height: 1rem;
					color: var(--color-raised-bg);
				}
			}
		}

		[type='checkbox']:checked + label span {
			background-color: var(--color-brand);

			:global(.icon) {
				display: unset;
			}
		}
	}
</style>
