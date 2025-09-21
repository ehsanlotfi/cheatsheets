#### Template Syntax
```
<!-- Loop -->
<div v-for="(item, i) in items" :key="i">{{ item }}</div>

<!-- If / Else -->
<p v-if="ok">Yes</p>
<p v-else-if="type==='b'">B</p>
<p v-else>No</p>

<!-- Show / Hide -->
<p v-show="visible">Visible</p>

<!-- Switch -->
<!-- Vue has no direct switch, use v-if / v-else-if -->

<!-- Data Binding -->
<p>{{ message }}</p>
<!-- Two-way -->
<input v-model="form.name" />

<!-- DOM & Refs -->
<input ref="inputEl" />
const inputEl = ref(null)

```
