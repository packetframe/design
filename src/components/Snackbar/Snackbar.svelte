<script lang="ts">
    import { fly } from 'svelte/transition'
    import { sineInOut } from 'svelte/easing'
    import { onMount, createEventDispatcher } from 'svelte'
    // import { validateHTMLColor, validateHTMLColorName } from "validate-color";

    /** should the snackbar be visible */
    export let open: boolean = false;
    /** status code for the snackbar */
    export let status: string | number = "200";
    /** message to be displayed */
    export let message: string = "";
    /** snackbar color */
    export let color: string = "green";
    /** callback function for when the close button is clicked.
     *  **PLEASE NOTE**: This will override the default close management function.
     *  If you do not want a controlled snackbar, use `on:close`.
     */
    export let handleClose: (e: Event) => any = null;
    /** number of ms before snackbar is removed */
    export let timeout: number = 4000;
    /** is this snackbar part of a snackbar group? designed for internal use */
    export let grouped: boolean = false;
    /** styles passed on to the snackbar */
    export let style: string = "";
    const dispatch = createEventDispatcher();
    const internalHandleClose = (e: Event) => {
        // Dispatch close event
        dispatch('close', {event: e, open});
        
        // Call handleClose if it has been set
        if (handleClose !== null) {
            handleClose(e);
            return;
        }
        open = false;
    }
    onMount(() => {
        
        if (grouped) {
            open = true;
        }
        if (timeout !== null) {
            const autoClose = setTimeout(internalHandleClose, timeout);
            return () => {clearTimeout(autoClose);}
        }
        
    })
    
    // TODO: decide whether to keep this?
    // $: if (!(validateHTMLColorName(color) || validateHTMLColor(color))) {
    //     color = "green"
    //     console.warn("<Snackbar> component was created with invalid value for 'color'")
    // }
    // //TODO: fix the above so it only warns once or twice maybe.
</script>

{#if open}
    <div
    class="pf-snackbar"
    transition:fly="{{delay: 50, duration: 400, y:100, easing: sineInOut }}" style="--color:{color};"
    class:grouped={grouped} class:ungrouped={!grouped}
    >
        <div class="pf-snackbar__wrapper" style={style}>
            <div class="pf-snackbar__status">{status}</div>
            <div class="pf-snackbar__message">{message.toLowerCase()}</div>
            <span class="pf-snackbar__icon material-icons" on:click={handleClose} style="--color:{color};">
                close
            </span>
        </div>
    </main>
{/if}

<style lang="scss" src="./Snackbar.scss" global>
</style>

<style>

</style>