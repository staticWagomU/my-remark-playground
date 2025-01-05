<script lang="ts">
  import { unified } from 'unified';
  import remarkParse from 'remark-parse';
  import {removePosition} from 'unist-util-remove-position'
  import remarkBudoux from 'remark-budoux';

  let textarea = '';
  function show() {
    const processor = unified().use(remarkBudoux).use(remarkParse);
    const ast = processor.parse(textarea);
    removePosition(ast, {force: true});
    return JSON.stringify(ast, undefined, 2);
  }
</script>

<textarea bind:value={textarea}></textarea>
<div style="white-space:pre-wrap;" >{show()}</div>
