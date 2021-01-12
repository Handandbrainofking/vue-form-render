# vue-form-render
Base on Vue 3.x, Quickly generates custom form configuration interfaces using JSON Schema.
## examples

[form-render live Demo](https://muwoo.github.io/kaer-form-render/)

![](./public/imgs/img.png)

## install
```shell
npm i kaer-form-render --save
```
`kear form render` depend on [Ant Design of Vue](https://2x.antdv.com/docs/vue/introduce-cn/)
to render from items.so before we use `kaer form render` we need to install `Ant Design of Vue` and import it to our project:
```vue
import { createApp } from 'vue'
import App from './App.vue'

import Antd from 'ant-design-vue';
import 'ant-design-vue/dist/antd.css';

const app = createApp(App);
app.use(Antd);
app.mount('#app');
```

## easy demo

```vue
<template>
  <div>
    <formRender
      :schema="schema"
      :formData="formData"
      @on-change="change"
      @on-validate="validate"
    />
  </div>
</template>

<script>
import {reactive, toRefs} from 'vue';

// render index
import FormRender from 'kaer-form-render';
// form render style
import 'kaer-form-render/lib/kaer-form-render.css';

export default {
  name: 'App',
  setup() {
    const state = reactive({
      schema: {
        type: 'object',
        properties: {
          string: {
            title: 'string',
            type: 'string',
            maxLength: 4,
            'ui:options': {
              placeholder: 'enter more than 4 characters',
            },
          }
        },
      },
      formData: {
        string: 'aaa'
      },
    });

    const change = (v) => {
      state.formData = v;
      console.log(v);
    }
    const validate = (v) => {
      console.log(v);
    }

    return {
      ...toRefs(state),
      change,
      validate,
    }
  },
  components: {
    FormRender,
  }
}
</script>

```

## Documentation
For extensive documentation see the examples folder or read it on [form-render](https://x-render.gitee.io/form-render/guide/design)

## Special thanks

this Project inspiration from [form-render](https://x-render.gitee.io/form-render/guide/design) 
but There is no similar framework for Vue 3.x



