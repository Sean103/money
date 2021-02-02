
<template>

    <Layout class-prefix="layout">
     
        <NumberPad :value.sync="record.amount" @submit="saveRecord"></NumberPad>
        <Types :value.sync="record.type"></Types>
        <Notes 
              fieldName="备注"
              placeholder="在这里输入备注"
              @update:value="onUpdateNotes"></Notes>
        <Tags></Tags>
   
    </Layout>        

</template>

<script lang="ts">
    import NumberPad from '@/components/Money/NumberPad.vue';
    import Types from '@/components/Money/Types.vue';
    import Notes from '@/components/Money/Notes.vue';
    import Tags from '@/components/Money/Tags.vue';

    import Vue from 'vue';
    import { Component } from 'vue-property-decorator';
    import store from '@/store/index2';
    
    
   

   
    
  

    @Component({

        components: {Tags, Notes, Types, NumberPad},

    })


    export default class Money extends Vue{
       
       
        recordList = store.recordList;
        record: RecordItem = {
            tags:[], notes: '', type:'-', amount: 0
        }
     
        onUpdateNotes(value: string) {
            this.record.notes = value;
        }

        saveRecord(){
           store.createRecord(this.record);
        }
       
        
        
    }
</script>
<style lang="scss">
    .layout-content {
        
        display: flex;
        flex-direction: column-reverse;


    }

</style>

<style lang="scss" scoped>













 

</style>