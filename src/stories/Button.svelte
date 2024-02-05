<script lang="ts">
	import { createEventDispatcher } from 'svelte';
  import './button.css';

  /**
   * Is this the principal call to action on the page?
   */
  export let primary = false;

  /**
   * What background color to use
   */
  export let backgroundColor: string | undefined = undefined;
  /**
   * How large should the button be?
   */
  export let size: 'small' | 'medium' | 'large' = 'medium';
  /**
   * Button contents
   */
  export let label: string = '';

  $: mode = primary ? 'storybook-button--primary' : 'storybook-button--secondary';

  $: style = backgroundColor ? `background-color: ${backgroundColor}` : '';

  const dispatch = createEventDispatcher<{testEvent: string}>();


function internalClick() {
  console.log('lets go')
  dispatch('testEvent', 'How to display in Actions tab?')
}
</script>

<button
  type="button"
  class={['storybook-button', `storybook-button--${size}`, mode].join(' ')}
  {style}
  on:click={internalClick}
>
  {label}
</button>


