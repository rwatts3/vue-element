<template>
  <div>
    <h2>Slots demo</h2>

    <div class="demo-card">
      <demo-slots>
        <span vue-slot="header">Heder slot passed from outside</span>
        <span>Default slot</span>
        <span vue-slot="footer">Footer slot passed from outside</span>
      </demo-slots>
    </div>

    <el-collapse v-model="activeNames">
      <el-collapse-item title="Description" name="1">
        <p>You can use default and named slots to pass content to Vue component.</p>
        <p>The only thing you have to know is, using named slots, instead of <code>slot="slotName"</code> you have to use <code>vue-slot="slotName"</code>.</p>

      </el-collapse-item>
      <el-collapse-item title="Custom Element HTML" name="2">
        <pre><code class="language-html">
{{HTML}}
        </code></pre>
      </el-collapse-item>
      <el-collapse-item title="Vue component passed to Vue-element" name="3">
        <pre><code class="language-html">
&#x3C;template&#x3E;
  {{vueTemplate}}
&#x3C;/template&#x3E;

&#x3C;script&#x3E;
  {{vueScript}}
&#x3C;/script&#x3E;
        </code></pre>
      </el-collapse-item>
      <el-collapse-item title="JavaScript - register with Vue-element" name="4">
        <pre><code class="language-javascript">
import DemoElement from 'DemoElement.vue';

Vue.element('demo-slots', DemoElement);
        </code></pre>
      </el-collapse-item>
    </el-collapse>
  </div>
</template>

<script>
  import Vue from 'vue';
  import DemoElement from 'demo/components/DemoSlots-component';

  export default {
    data() {
      return {
        activeNames: ['1'],
        HTML: (
`<demo-slots>
  <span vue-slot="header">Heder slot passed from outside</span>
  <span>Default slot</span>
  <span vue-slot="footer">Footer slot passed from outside</span>
</demo-slots>`
        ),
        vueTemplate: (
`<div>
    <el-alert title="" type="info">
      <slot name="header">No HEADER slot content passed (this is default value)</slot>
    </el-alert>

    <p>This is text from inside of the element</p>

    <el-alert title="" type="info">
      <slot>No DEFAULT slot content passed (this is default value)</slot>
    </el-alert>

    <el-alert title="" type="info">
      <slot name="footer">No FOOTER slot content passed (this is default value)</slot>
    </el-alert>
  </div>`
        ),
        vueScript: 'export default {};'
      };
    },
    methods: {
      registerCustomElement() {
        Vue.element('demo-slots', DemoElement);
      }
    }
  };
</script>

