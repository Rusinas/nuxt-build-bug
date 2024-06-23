<template>
  <div>
    <div class="editor" ref="editor_ref"></div>
  </div>
</template>

<script lang="ts" setup>
import {
  $createParagraphNode,
    $createTextNode,
    $getRoot,
    createEditor,
    type CreateEditorArgs,
} from 'lexical'

const config: CreateEditorArgs = {
    editable: false,
    namespace: 'test',
    onError: console.error
}

const editor_ref = ref()

onMounted(() => {
    editor.setRootElement(editor_ref.value)
})

const editor = createEditor(config)

editor.update(() => {
  const paragraph = $createParagraphNode()
  const text = $createTextNode('HELLO WORLD')
  paragraph.append(text)
  $getRoot().append(paragraph)
  $getRoot().selectEnd()
})
</script>
