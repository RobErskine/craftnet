<template>
    <field :errors="errors" class="c-checkbox-set">
        <fieldset>
            <legend>{{ label }}</legend>

            <div v-if="instructions" class="instructions">
                <p>{{ instructions }}</p>
            </div>

            <ul>
                <li v-for="(option, index) in options" :key="index">
                    <label>
                        <input type="checkbox" v-model="localValue" :value="option.value" @change="$emit('input', localValue)">
                        {{ option.label }}
                    </label>
                </li>
            </ul>
        </fieldset>
    </field>
</template>

<script>
    export default {
        props: {
            options: {
                type: Array,
                default: null,
            },
            label: {
                type: String,
                default: null,
            },
            instructions: {
                type: String,
                default: null,
            },
            value: {
                type: String,
                default: null,
            },
            errors: {
                type: Array | Boolean,
                default: null,
            },
        },

        data() {
            return {
                localValue: []
            }
        },

        mounted() {
            this.localValue = JSON.parse(JSON.stringify(this.value))
        }
    }
</script>

<style lang="scss">
    .c-checkbox-set {
        fieldset {
            ul {
                @apply .list-reset .pt-2 .pl-4;

                input {
                    @apply .mr-2;
                }
            }
        }
    }
</style>
