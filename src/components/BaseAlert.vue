<template>
  <div :class="baseClass">
    
   <slot/>

    <button @click="onClick()"> <!--@click mesma coisa que v-on:click -->
    X
  </button>

  </div>
</template>

<script>
  export default {
    props: {
      variant: {
        type: String,
        default: ""
      },
    },

    methods: {
      onClick(){
        this.$emit('close')
        console.log('clicou');
      }
    },


    computed: {
      baseClass() {
        return [
          'alert',
          this.variant ? `alert-${this.variant}` : ''
          //this é a instânica do componente, que pode acessar tudo e também a instância da propriedade (props).
          // Se existir variante, imprima alert- e o nome da variante, se não existir variante, imprima vazio.
        ]
      }
    }

    }
  
</script>

<style scoped>
  .alert {
    display: flex;
    justify-content: space-between;
    padding: 10px;
    border-radius: 10px;
    color: gray;
    background: bisque;

  }
  .alert-success {
    background: rgb(187, 144, 228);
    color: white;
    border-radius: 10px;
  }

  .alert-danger {
    background: rgb(28, 136, 136);
    color: white;
    border-radius: 10px;
  }
</style>