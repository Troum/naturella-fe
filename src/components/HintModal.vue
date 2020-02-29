<template lang="pug">
    b-modal#hint( title="Фото номер чека" hide-footer centered)
        b-row.p-0
            b-col.mx-auto.p-0.text-center( cols="11" )
                img.img-fluid( src="../assets/images/check-photo.jpg" alt="Check Photo")
</template>

<script>
    export default {
        name: "HintModal"
    }
</script>
