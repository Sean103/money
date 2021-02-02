
<template>

    <Layout class-prefix="layout">
     
        <NumberPad :value.sync="record.amount" @submit="saveRecord"></NumberPad>
        <Tabs :data-source="recordTypeList"
          :value.sync="record.type"/>

        <Notes 
              fieldName="备注"
              placeholder="在这里输入备注"
              @update:value="onUpdateNotes"></Notes>
        <Tags></Tags>
    
   
    </Layout>        

</template>

<script lang="ts">
    import NumberPad from '@/components/Money/NumberPad.vue';
    
    import Notes from '@/components/Money/Notes.vue';
    import Tags from '@/components/Money/Tags.vue';

    import Vue from 'vue';
    import { Component } from 'vue-property-decorator';
    import Tabs from '@/components/Tabs.vue';
    import recordTypeList from '@/constants/recordTypeList';
    
    
    
   

   
    
  

    @Component({
        components: {Tabs,Tags, Notes, NumberPad},
    })


    export default class Money extends Vue{
        get recordList() {
            return this.$store.state.recordList;
        }
        recordTypeList = recordTypeList;

        record: RecordItem = {
            tags:[], notes: '', type:'-', amount: 0
        }
        created() {
            this.$store.commit('fetchRecords');
        }
     
        onUpdateNotes(value: string) {
            this.record.notes = value;
        }

        saveRecord(){
           this.$store.commit('createRecord', this.record);
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