<template>
    <div class = "page-success">
        <div class = "columns is-multiline">
            <div class = "column is-12">
                <h1 class = "title">Your order has been placed! Thank you!</h1>
            </div>
        </div>
    </div>
</template>
<script>

export default {
    name: "Success",
    mounted(){
        document.title = "Success | StickerFiend"
    },
}
</script>
