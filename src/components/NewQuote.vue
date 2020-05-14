<template>
    <div>
        <div class="row">
            <div class="col-md-8 col-md-offset-2 mb-4">
                <div class="form-group">
                    <label for="quote">Your Quote</label>
                    <textarea id="quote" cols="3" rows="1" class="form-control" v-model="quote"></textarea>
                </div>
                <div class="form group">
                    <button class="btn btn-primary btn-sm" @click="addNewQuote">
                        Add Quote
                    </button>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: ['quotes'],
    data() {
        return {
            quote: '',
        }
    },

    methods: {
        addNewQuote() {
            this.$emit('newQuoteAdded', this.quote);
            this.quote = '';
        }
    }
}
</script>