<template>
    <div class="component">
        <h3>You may view the User Details here</h3>
        <p>Many Details</p>
        <p>User Name: {{ name }}</p>
        <p>User Age: {{ userAge }}</p>
        <button @click="resetName">Reset Name</button>
    </div>
</template>

<script>
import {eventBus} from '../main';
    export default {
        props: {
          name: String,
          userAge: Number
        },
        methods: {
            // switchName(){
            //     return this.name.split("").reverse().join("");
            // },
            resetName() {
                this.name = 'Max';
                this.$emit('nameWasReset', this.name);
            }
        },
        created() {
          eventBus.$on('ageWasEdited', (age) => {
              this.userAge = age;
          });
        }
    }
</script>

<style scoped>
    .component {
        background-color: lightcoral;
    }
</style>
