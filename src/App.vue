<template>
    <div class="container">
        <app-header :quoteCount="quotes.length" :maxQuotes="maxQuotes"></app-header>
        <app-new-quote @quoteAdded="newQuote"></app-new-quote>
        <div class="row" v-if="quotes.length >= 10">
            <div class="col-sm-12 text-center">
                <div class="alert alert-danger">Remove a quote before adding more.</div>
            </div>
        </div>
        <hr>
        <app-quote-grid :quotes="quotes" @quoteDeleted="deleteQuote"></app-quote-grid>
        <div class="row">
            <div class="col-sm-12 text-center">
                <hr>
                <div class="alert alert-info">Info: Click on a quote to delete it</div>
            </div>
        </div>
    </div>
</template>

<script>
    import QuoteGrid from './components/QuoteGrid.vue';
    import NewQuote from './components/NewQuote.vue';
    import Header from './components/ProgressBar.vue';
    export default {
        data(){
            return {
                maxQuotes: 10,
                quotes: ['Just a Quote', 'Another quote for you', 'This is the third quote']
            }
        },
        components: {
            'app-quote-grid' : QuoteGrid,
            'app-new-quote'  : NewQuote,
            'app-header'     : Header
        },
        methods:
            {
                newQuote(quote){
                    if(this.quotes.length >= this.maxQuotes){
                        return;
                    }

                    if(!quote){
                        return alert('Please enter a quote');
                    }
                    this.quotes.push(quote);
                },
                deleteQuote(index) {
                    this.quotes.splice(index, 1);
                }
            }
    }
</script>

<style>
</style>
