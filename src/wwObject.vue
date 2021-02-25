<template>
    <div hidden id="snipcart" :data-api-key="content.apiKey"></div>
</template>

<script>
export default {
    props: {
        content: { type: Object, required: true },
    },
    wwDefaultContent: {
        // MWJiMjRjMmMtOGExNC00NDlkLTg1NTktMDkzMmVlZGQ4Y2VlNjM3NDkzMzEyMTkxNjI5Mjk3
        apiKey: '',
    },
    watch: {
        'content.apiKey'() {
            this.initSnipcart();
        },
    },
    methods: {
        initSnipcart() {
            let preconnects = ['https://app.snipcart.com', 'https://app.snipcart.com'];
            preconnects.forEach(link => {
                const el = document.createElement('link');
                el.setAttribute('rel', 'preconnect');
                el.setAttribute('href', link);
                document.head.appendChild(el);
            });

            let snipcart = document.createElement('script');
            snipcart.setAttribute('async', '');
            snipcart.setAttribute('src', 'https://cdn.snipcart.com/themes/v3.0.30/default/snipcart.js');
            document.body.appendChild(snipcart);
        },
    },
};
</script>

<style lang="scss">
@import './snipcart.css';
</style>
