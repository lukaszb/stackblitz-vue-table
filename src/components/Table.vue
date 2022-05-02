<script lang="tsx">
import { isFunction } from "lodash";
import { defineComponent, getCurrentInstance } from "vue";
import Column from "./Column.vue";

export default defineComponent({
  props: {
    data: Array,
  },
  setup(props) {
    const getChildren = () => {
      const instance = getCurrentInstance();
      const children = instance?.slots.default?.() || [];
      return children;
    };
    const children = getChildren();
    console.log(children);
    Object.assign(window, { children });
    return () => (
      <table>
        <thead>
          <tr>
            {children.map((child: any) => {
              if (isFunction(child.children.header)) {
                return <th>{child.children.header()}</th>;
              } else {
                return <th>{child.props.header}</th>;
              }
            })}
          </tr>
        </thead>
        <tbody>
          {props.data?.map((item: any) => (
            <tr>
              {children.map((child: any) => {
                return <td>{child.children.default({ item })}</td>;
              })}
            </tr>
          ))}
        </tbody>
      </table>
    );
  },
});
</script>
