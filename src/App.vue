<template>
    <div class="container">
        <app-header :quoteCount="quotes.length" :maxQuotes="maxQuotes"></app-header>
        <app-new-quote @quoteAdded="newQuote"></app-new-quote>
        <app-quote-grid :quotes="quotes" @quoteDeleted="deleteQuote"></app-quote-grid>
        <div class="row">
            <div class="col-sm-12 text-center">
                <div class="alert alert-info">
                    click on a Quote to delete it!
                </div>
            </div>
        </div>
    </div>

</template>

<script>
    import QuoteGrid from './components/QuotesGrid.vue';
    import NewQuote from './components/NewQuote.vue';
    import Header from './components/Header.vue';

    export default {
        data: function() {
            return {
                quotes: [
                    'Just a Quote to see something' 
                ],
                maxQuotes: 10
            }
        },
        methods: {
            newQuote(quote) {
                if (this.quotes.length >= this.maxQuotes) {
                    return alert('Remove some quotes');
                }
                
                this.quotes.push(quote);
                console.log("size added " + this.quotes.length);
            },
            deleteQuote(index) {
                console.log("index " + index);
                this.quotes.splice(index, 1);
                console.log("size delete: " + this.quotes.length);
            }
        },
        components: {
            appQuoteGrid: QuoteGrid,
            appNewQuote: NewQuote,
            appHeader: Header
        }
    }
</script>

<style>
</style>
