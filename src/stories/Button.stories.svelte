<script context="module" lang="ts">
    import { userEvent, within, waitFor } from '@storybook/testing-library';
	import Button from "./Button.svelte";

    export const meta = {
        title: 'Buttons',
        tags: ['autodocs'],
        
        component: Button,
        args: {
            size: 'medium',
            label: 'test-story',
        },
        play: async ({ args, canvasElement }) => {
            const canvas = within(canvasElement);
            const buttons = canvas.getAllByRole('button');
            const button = buttons[0];
            const eventPromise = new Promise((resolve) => {
                button.addEventListener('testEvent', resolve, { once: true });
            });
            await Promise.all([
                userEvent.click(button),
                waitFor(() => eventPromise)
            ])
            
            // await waitFor(() => expect(args.on).toHaveBeenCalled());
        },
    } satisfies Meta<Button>;;

</script>

<script lang="ts">
    import { Story } from '@storybook/addon-svelte-csf';
	import type { Meta } from '@storybook/svelte';

</script>

<Story name="Primary" let:args>
    <Button {...args} on:testEvent/>
    
</Story>
