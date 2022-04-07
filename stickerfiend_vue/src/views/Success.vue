
   
<template>
    <div class="page-success">
        <div class="columns is-multiline">
            <div class="column is-12 ">
                <h1 class="title" style="color:white">Thank you</h1>

                <p style="color:white">Your order will be processed within 48 hours</p>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Success',
    mounted() {
        document.title = 'Success | StickerFiend'
    },
}
</script>
