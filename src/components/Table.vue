<script lang="tsx">
import { defineComponent } from 'vue'

export default defineComponent({
  props: {
    data: Array
  },
  setup(props) {
    return () => (
      <div>Hello world</div>
    )
  }
})
</script>
