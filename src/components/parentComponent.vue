<template>
  <div>

    <child-component 
      :buttonClickedStatus="buttonClickedStatus" 
      @customNamedEmit="changeSubmitStatus"
    >
      {{ buttonClickedStatus }}
    </child-component>
 
  </div>
</template>

<script>
import ChildComponent from './childComponent.vue';
export default {
  name: "ParentComponent",
  components: {
    ChildComponent
  },
  data () {
    return {
      buttonClickedStatus: 'Click me'
    }
  },
  methods: {
    changeSubmitStatus (value) {
      console.log(value);
      this.buttonClickedStatus = value;
    }
  }
};
</script>