<template>
    <div id="quotes-progress-bar">
        <h3>Quotes Added</h3>
        <div class="progress">
            <div
                class="progress-bar"
                role="progressbar"
                :style="{ width: (quoteCount / maxQuotes) * 100 + '%' }"
            >
                <span v-if="quoteCount > 0">{{ quoteCount }} / {{ maxQuotes }}</span>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        props: ['quoteCount', 'maxQuotes']
    }
</script>
