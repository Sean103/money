<template>
    <div>
        <label  class="notes">
            <span class="name">{{this.fieldName}}</span>
            <input type="text"
                :value="value"
                @input="onValueChanged($event.target.value)"
                :placeholder="placeholder">
        </label>
    </div>
</template>
Vue
<script lang="ts">
import Vue from 'vue';
import { Component, Prop } from 'vue-property-decorator';

@Component
    export default class Notes extends Vue{
        
        @Prop({default: ''}) readonly value!: string;

        @Prop({required: true}) fieldName!: string;
        @Prop() placeholder?: string;


     
        onValueChanged(value: string) {
            this.$emit('update:value', value);
       }
    }
</script>

<style lang="scss" scoped>

    .notes{
        font-size: 14px;
        padding-left: 16px;
        display: flex;
        align-items: center;
        .name{
            padding-right: 16px;
        }
        input{
            height: 40px;
            flex-grow: 1;
            border: none;
            background: transparent;
            padding-right: 16px;

        }
    }


</style>