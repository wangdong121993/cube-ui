## Introduction

cube-ui is an elegant mobile component library based on Vue.js.

### Features

- Extracted from Didi interior component library and has been put to business test for more than one year
- Every component has full unit tests to provide assurance for continuous integration
- Pursue the perfection of the interactive experience, which makes cube-ui close to native components
- Support post-compile and importing on demand, lightweight and flexible

### Components

#### Basic

- [Button](#/en-US/docs/button)
- [Checkbox](#/en-US/docs/checkbox)
- [CheckboxGroup](#/en-US/docs/checkbox-group)
- [Loading](#/en-US/docs/loading)
- [Tip](#/en-US/docs/tip)

#### Layer

- [Toast](#/en-US/docs/toast)
- [Picker](#/en-US/docs/picker)
- [TimePicker](#/en-US/docs/time-picker)
- [Dialog](#/en-US/docs/dialog)
- [ActionSheet](#/en-US/docs/action-sheet)

All the layer components can be invoked by components and API, let's take `Toast` as an example:

Component invoking:

```html
<template>
  <cube-button @click="showToast">show toast</cube-button>
  <cube-toast ref="toast" :txt="toastTxt"></cube-toast>
</template>
<script>
  export default {
    data() {
      return {
        toastTxt: 'toast content'
      }
    },
    methods: {
      showToast() {
        this.$refs.toast.show()
      }
    }
  }
</script>
```

API invoking：

```html
<template>
  <cube-button @click="showToast">show toast</cube-button>
</template>
<script>
  export default {
    data() {
      return {
        toastTxt: 'toast content'
      }
    },
    methods: {
      showToast() {
        this.$createToast({
          txt: this.toastTxt
        }).show()
      }
    }
  }
</script>
```
Both are pretty good but we recommend the latter, namely using `$createXxYy` API to invoke; By API invoking, the popup layer is attached to `body` element whose advantage is that it wouldn't be affected by outer styles. If using component invoking, it's fairly easy to be affected by outer styles like `transform`, `overflow`, etc.

Pay attention that the name of the API is `$create` + `${component name}`. For example, the API of `ActionSheet` component is `$createActionSheet`.

#### Scroll

- [Scroll](#/en-US/docs/scroll)
- [Slide](#/en-US/docs/slide)
- [IndexList](#/en-US/docs/index-list)

Scroll Components are all implemented based on [better-scroll](https://github.com/ustbhuangyi/better-scroll) and `Scroll` Component is the encapsulation of better-scroll.

### Modules

cube-ui has some special modules besides components.

#### style
The style module.
If you are under the circumstance of importing components on demand, then it is recommended to import this module in entry file because it contains basic reset, basic common styles and built-in icons.

For details, see [style module](#/en-US/docs/style).

#### create-api

Sometimes, developers may need to let their own encapsulated components support API invoking as well. At this time they can import create-api module or use the global interface `Cube.createAPI` to achieve the purpose.


For details, see [create-api module](#/en-US/docs/create-api)。

#### better-scroll

[better-scroll](https://github.com/ustbhuangyi/better-scroll) is a library in `cube-ui`'s dependencies. To avoid duplicately importing, we expose the module.

For more detailed use, please refer to [official documentation](https://ustbhuangyi.github.io/better-scroll/#/zh)。