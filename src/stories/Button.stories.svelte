<script context="module">
	import Button from "./Button.svelte";

    export const meta = {
        title: 'Buttons',
        tags: ['autodocs'],
        
        component: Button,
        args: {
            size: 'medium',
            label: 'test-story'
        },
  
    };
    function handleClick() {
        console.log('click called')
    }
</script>

<script lang="ts">
    import { Story } from '@storybook/addon-svelte-csf';

</script>

<Story name="Primary" let:args>
    <Button {...args} on:click on:click={handleClick} />
    
</Story>
