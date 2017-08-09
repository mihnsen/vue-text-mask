<template>
  <div class="container">
    <form class="form-horizontal">
      <div class="form-group">
        <label for="1" class="col-sm-4 control-label">Masked input</label>

        <div class="col-sm-8">
          <masked-input
            type="text"
            name="phone"
            class="form-control"
            v-model="phone"
            :mask="['(', /[1-9]/, /\d/, /\d/, ')', ' ', /\d/, /\d/, /\d/, '-', /\d/, /\d/, /\d/, /\d/]"
            @keypress="handleKeypress">
          </masked-input>
        </div>
      </div>

      <div class="form-group">
        <label for="2" class="col-sm-4 control-label">Model</label>

        <div class="col-sm-8">
          <input
            disabled
            type="text"
            v-model="phone"
            class="form-control">
        </div>
      </div>

      <div class="form-group">
        <label for="4" class="col-sm-4 control-label">Current pressed key:</label>

        <div class="col-sm-8 text-left">
          <p class="form-control-static">{{ pressedKey }}</p>
        </div>
      </div>
    </form>
  </div>
</template>

<script>
  import MaskedInput from '../src/vueTextMask'

  export default {
    name: 'app',

    components: {
      MaskedInput
    },

    methods: {
      handleKeypress (e) {
        this.pressedKey = e.key;
      }
    },

    data () {
      return {
        phone: '',
        pressedKey: null,
      }
    }

  }
</script>
