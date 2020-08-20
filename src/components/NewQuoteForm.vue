<template>
    <div class="row">
        <form>
            <div class="form-group col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
                <label>Quote</label>
                <textarea class="form-control" rows="3" v-model="quote"></textarea>
            </div>
            <div class="form-group col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3 text-center">
                <button class="btn btn-primary" @click.prevent="createNew" :disabled="emptyQuote()">Add Quote</button>
            </div>
        </form>
    </div>
</template>

<script>
    export default {
        props: ['clearTextarea'],
        data: () => ({ quote: '' }),
        methods: {
            createNew() {
                if (!this.emptyQuote()) {
                    this.$emit('quoteAdded', this.quote);
                    if (this.clearTextarea) this.quote = '';
                }
            },
            emptyQuote() { return this.quote === ''; }
        }
    }
</script>
