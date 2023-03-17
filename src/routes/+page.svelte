<script lang="ts">
    import {onMount} from "svelte";
    import "@smui/menu/bare.css";
    import EnhancedSelect from "../lib/EnhancedSelect.svelte";

    onMount(()=>{
    })

    let mark: string = '';
    let dicMarks = [
        {
            code: "1",
            value: "优 (总体合格率大于90%）"
        },
        {
            code: "2",
            value: "良 (总体合格率80%-90%）"
        },
        {
            code: "3",
            value: "合格 (总体合格率大于60%-80%）"
        },
        {
            code: "3",
            value: "不合格 (总体合格率低于60%）"
        }
    ]

</script>
<div style="width: 500px">
    <EnhancedSelect variant="outlined" check$style="width: 100%;" menu$style="height: 180px" emptyKey=''
                    emptyText="请选择"
                    bind:value={mark} list={dicMarks} opKey="code" opValue="value"/>
</div>



