<script lang="ts">

    import {createEventDispatcher} from 'svelte';
    import {onMount} from 'svelte'
    import Select, {Option} from '@smui/select';

    export let check$style;
    export let list;
    export let value;
    export let label:string = null;
    export let opKey;
    export let opValue;
    export let invalid:boolean = false;
    export let disabled:boolean = false;
    export let emptyText:string = '';
    export let emptyKey:string = ' ';
    export let menu$style:string = '';
    export let variant = 'standard';

    let dispatch = createEventDispatcher();

    let lastValue:any = value;

    $: if (value !== lastValue) {
        console.debug('选择值发生变化')
        dispatch('change', {value});
        lastValue = value;
    }


    onMount(async () => {
        lastValue = value;
    });

</script>

<Select {disabled} helperText$style="{invalid ? 'color: var(--mdc-theme-error, #b00020);' : ''}" style={check$style}
        {menu$style} {invalid} {variant} bind:value={value} label="{label}" on:blur}>
    {#if emptyText!=null}
        <Option value={emptyKey}>{emptyText}</Option>
    {/if}
    {#if list}
    {#each list as item}
        <Option value={item[opKey]}>{item[opValue]}</Option>
    {/each}
    {/if}
</Select>