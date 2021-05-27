<template>
<base-dialog v-if="inputIsInvalid" title="INVALID INPUT">
    <template #default>
      <p>Check Please, Atleast one input is invalid :(</p>
      <p>Please Cheack all input ad enter atlease some character.</p>
    </template>

    <template #actions>
        <base-button @click="closeDialog">OK</base-button>
    </template>


</base-dialog>


  <base-card>
    <form @submit.prevent="sumbitData">
      <div class="form-control">
        <label for="title">Title</label>
        <input ref="title" id="title" name="title" type="text" />
      </div>
       <div class="form-control">
        <label for="description">Description</label>
        <textarea ref="desc" id="description" name="description" rows="3" />
      </div>
       <div class="form-control">
        <label for="link">Link</label>
        <input ref="link" id="link" name="link" type="url" />
      </div>
       <div>
           <base-button type="submit">Add Resource</base-button>
      </div>
    </form>
  </base-card>
</template>


<script>
export default {
    inject:['addResource'],
    data() {
        return {
            inputIsInvalid:false
        }
    },
    methods: {
        sumbitData(){
           

            const enteredTitle= this.$refs.title.value;
            const enteredDescription= this.$refs.desc.value;
            const enteredLink= this.$refs.title.link;
            const id= new Date().toISOString()

             if(enteredTitle.trim()==='' ||enteredDescription.trim()=== '' || enteredLink===''  ){
              this.inputIsInvalid= true
                return;
            }

            const enterdBundle={
                if: id,
                title: enteredTitle,
                description:enteredDescription,
                link: enteredLink
            }
            // this.$emit('emitEnteredBundle',enterdBundle)
            // or use inject
            this.addResource(enterdBundle)
        },
        closeDialog(){
             this.inputIsInvalid= false
        }
    },
}
</script>

<style scoped>
label {
  font-weight: bold;
  display: block;
  margin-bottom: 0.5rem;
}

input,
textarea {
  display: block;
  width: 100%;
  font: inherit;
  padding: 0.15rem;
  border: 1px solid #ccc;
}

input:focus,
textarea:focus {
  outline: none;
  border-color: #3a0061;
  background-color: #f7ebff;
}

.form-control {
  margin: 1rem 0;
}
</style>