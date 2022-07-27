<template>
    <select v-model="key" @change="$emit('select', key)">
        <option value="">{{ placeholder }}</option>
        <option v-for="option in options" :key="option.value" :value="option.value">{{ option.text }}</option>
    </select>
</template>

<script>
export default {
    name: 'StandardSelect',
    data() {
        return {
            key: '',
        }
    },
    props: {
        placeholder: String,
        options: Array,
    },

}
</script>

<style lang="scss" scoped>
select {
    margin-left: 20px;
}
</style>