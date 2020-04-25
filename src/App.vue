<template>
    <div id="app">
        <Panel>
            <HelloWorld msg="Bombino basic" />
        </Panel>
        <Menus
            refresh
            :context="[
                {
                    label: 'Test script',
                    callback: this.testScript,
                },
            ]"
        />
    </div>
</template>

<script>
    // Utility components, see here:
    // https://github.com/Inventsable/lokney
    import { Menus, Panel } from "lokney";
    /*
  Panel component above also includes:
    - Starlette UI theme and color library: 
      https://github.com/Inventsable/starlette
    - CEP-Spy identification and app utility:
      https://github.com/Inventsable/cep-spy
 These are still installed into this panel and can be used when needed like so:
 import spy from 'cep-spy'

 NOTES: 
  - Starlette is already active in your panel! There's no need to initialize it.
  - Need CSInterface or a script? You can use the script-path attribute of Panel to launch scripts or utilities:
    https://github.com/Inventsable/lokney/tree/master/components/Panel
*/
    import { evalScript } from "cluecumber";
    export default {
        name: "App",
        components: {
            Menus,
            Panel,
            HelloWorld: require("./components/HelloWorld.vue").default,
        },
        methods: {
            async testScript() {
                console.log("Testing script...");
                let result = await evalScript("testScript()");
                console.log(`Result is ${result}`);
            },
        },
    };
</script>

<style></style>
