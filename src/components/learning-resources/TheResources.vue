<template>
<base-button>
<vue3-autocounter class="counter" ref='counter' :startAmount='0' :endAmount='countNumberOfReources()' :duration='2' prefix='Total Showing ' suffix=' Resources' separator=',' decimalSeparator='.' :decimals='0' :autoinit='true' @finished='alert(`Counting finished!`)'/>
</base-button>
 
    <base-card>
    <base-button @click="selectTab('stored-resource')" :mode="selectedStoredTab" >Stored Resources</base-button>
    <base-button @click="selectTab('add-resource')" :mode="selectedAddTab">Add Resources</base-button>
    </base-card>
    <keep-alive>
    <component :is="selectedTab"></component>
    </keep-alive>
</template>

<script>
import Vue3autocounter from 'vue3-autocounter';
import StoredResource from   './StoredResources'
import AddResource from   './AddResource'
export default {
    components:{
        StoredResource,
        AddResource,
         'vue3-autocounter': Vue3autocounter
    },
    computed:{
        selectedStoredTab(){
            return this.selectedTab==='stored-resource' ? null : 'flat'
        },
         selectedAddTab(){
            return this.selectedTab==='add-resource' ? null : 'flat'
        }
    },
    data() {
        return {
            selectedTab:'stored-resource',
             storedResource: [
        {
          id: 'official-guide',
          title: 'Official-Guide',
          description: 'The official Vue Js documentation!',
          link: 'https://vuejs.org'
        },
        {
          id: 'google',
          title: 'Google',
          description: 'Learn to google...',
          link: 'https://www.google.co.in'
        }
      ]
        }
    },
    methods: {
        selectTab(cmp){
            this.selectedTab =cmp;
        },
        addResources(resourceBundle){
            this.storedResource.unshift(resourceBundle);
             this.selectedTab='stored-resource'
        },
        removeResource(resId){
            const searchedIndex = this.storedResource.findIndex(res=> res.id === resId);
            this.storedResource.splice(searchedIndex,1)
        },
        countNumberOfReources(){
            return this.storedResource.length;
        }
    },
    provide(){
        return{
            resources: this.storedResource,
            addResource: this.addResources,
            removeResource:this.removeResource,
            resourceCounter:this.countNumberOfReources
        }
    }
}
</script>

<style scoped>
    .counter{
        font-size:1.3rem;
        /* border-radius: 10px; */
        background: rgb(255, 255, 255);
        color:black;
        box-shadow: 2px 4px 8px black;
        
        font-weight: bolder;
    }
</style>