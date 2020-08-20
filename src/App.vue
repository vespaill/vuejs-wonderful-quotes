<template>
    <div class="container">
        <app-header :quoteCount="quotes.length" :maxQuotes="maxQuotes"></app-header>
        <app-new-quote-form @quoteAdded="newQuote" :clearTextarea="quotes.length < maxQuotes"></app-new-quote-form>
        <app-quote-grid :quotes="quotes" @quoteDeleted="deleteQuote"></app-quote-grid>
        <div class="row">
            <div class="col-sm-12 text-center">
                <div class="alert alert-info">
                    Info: Click on a Quote to delete it
                </div>
            </div>
        </div>
        <div class="row">
            <div class="col-sm-12 text-center">
                <button :disabled="!quotes.length" class="btn btn-danger" @click="deleteAllQuotes">Delete All Quotes</button>
            </div>
        </div>

    </div>
</template>

<script>
    import Header from './components/Header.vue';
    import NewQuoteForm from './components/NewQuoteForm.vue';
    import QuoteGrid from './components/QuoteGrid.vue';

    export default {
        data: () => ({
            quotes: ['Just a Quote to start with something!'],
            maxQuotes: 10,
        }),
        components: {
            appHeader: Header,
            appNewQuoteForm: NewQuoteForm,
            appQuoteGrid: QuoteGrid
        },
        methods: {
            newQuote(quote) {
                if (this.quotes.length >= this.maxQuotes) {
                    alert('Too many Quotes! Delete some before adding new ones!');
                } else {
                    this.quotes.push(quote);
                }
            },
            deleteQuote(index) {
                this.quotes.splice(index, 1);
            },
            deleteAllQuotes() {
                this.quotes.splice(0, this.quotes.length);
            }
        }
    }
</script>
