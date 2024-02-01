<script context="module">
	import Button from "./Button.svelte";
    import { withActions } from '@storybook/addon-actions/decorator';

    export const meta = {
        title: 'Buttons',
        tags: ['autodocs'],
        
        component: Button,
        args: {
            size: 'medium',
            label: 'test-story'
        },
        parameters: {
        actions: {
            handles: ['custom', 'click'],
        },
  },
  decorators: [withActions],
    };
</script>

<script lang="ts">
    import { Story } from '@storybook/addon-svelte-csf';

</script>

<Story name="Primary" let:args>
    <Button {...args} on:click={args.onClick} />
    
</Story>
