<template>
    <div>
        <div class="row">
            <div class="text-danger text-center" v-if="quotes.length === 0">
                No quotes found. Please add some
            </div>
            <div class="col-sm-12 col-md-3 col-lg-4" v-for="(quote, index) in quotes" :key='index'>
                <div class="card" @click="deleteQuote(index)">
                    <div class="card-body">
                        #{{ index }} {{ quote }}
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: ['quotes'],
    methods: {
        deleteQuote(index) {
            this.$emit('deleteQuote', index);
        }
    }
}
</script>

<style scoped>
    .card {
        cursor: pointer;
    }
</style>