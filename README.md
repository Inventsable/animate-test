# animate-test

## Getting it working:

```bash
# in .../CEP/extensions/
git clone https://github.com/Inventsable/animate-test.git
cd animate-test
npm run serve
```

Then launch the host app and find in Windows > Extensions > animate-test.

For styling in Animate, `starlette` assumes the lightest/darkest variant. If incorrect, right click the panel and select `Switch Themes`, then all future mounts of the panel should appear in the correct theme. `Switch Themes` is an exclusive menu item of `lokney` combined with `starlette` and will only appear in Animate when using the `Menus` component.

## See the App.vue file for cluecumber use:

```html
<template>
  <div id="app">
    <Panel>
      <HelloWorld msg="Bombino basic" />
    </Panel>
    <Menus refresh :context="[
      {
        label: 'Test script',
        callback: this.testScript
      }
    ]" />
  </div>
</template>

<script>
import { evalScript } from 'cluecumber'
export default {
  name: "App",
  components: {
    Menus,
    Panel,
    HelloWorld: require('./components/HelloWorld.vue').default
  },
  methods: {
    async testScript() {
      console.log('Testing script...')
      let result = await evalScript('testScript()');
      console.log(`Result is ${result}`)
    }
  }
};
</script>
```