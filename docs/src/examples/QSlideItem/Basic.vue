<template>
  <div class="q-pa-md" style="max-width: 350px">
    <q-list bordered separator>

      <q-slide-item @left="onLeft" @right="onRight">
        <q-icon slot="left" name="done" />
        <q-icon slot="right" name="alarm" />

        <q-item>
          <q-item-section avatar>
            <q-avatar color="primary" text-color="white" icon="bluetooth" />
          </q-item-section>
          <q-item-section>Icons only</q-item-section>
        </q-item>
      </q-slide-item>

      <q-slide-item @left="onLeft" @right="onRight">
        <div slot="left">Left</div>
        <div slot="right">Right content.. long</div>

        <q-item>
          <q-item-section avatar>
            <q-avatar>
              <img src="https://cdn.quasar-framework.org/img/avatar6.jpg">
            </q-avatar>
          </q-item-section>
          <q-item-section>Text only</q-item-section>
        </q-item>
      </q-slide-item>

      <q-slide-item @left="onLeft" @right="onRight">
        <div slot="left" class="row items-center">
          <q-icon left name="done" /> Left
        </div>
        <div slot="right" class="row items-center">
          Right content.. long <q-icon right name="alarm" />
        </div>

        <q-item>
          <q-item-section avatar>
            <q-avatar>
              <img src="https://cdn.quasar-framework.org/img/avatar4.jpg">
            </q-avatar>
          </q-item-section>
          <q-item-section>Text and icons</q-item-section>
        </q-item>
      </q-slide-item>

    </q-list>
  </div>
</template>

<script>
export default {
  methods: {
    onLeft ({ reset }) {
      this.$q.notify('Left action triggered. Resetting in 1 second.')
      this.finalize(reset)
    },

    onRight ({ reset }) {
      this.$q.notify('Right action triggered. Resetting in 1 second.')
      this.finalize(reset)
    },

    finalize (reset) {
      this.timer = setTimeout(() => {
        reset()
      }, 1000)
    }
  },

  beforeDestroy () {
    clearTimeout(this.timer)
  }
}
</script>
