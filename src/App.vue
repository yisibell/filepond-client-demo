<template>
  <main>
    <input ref="fileInput" type="file" name="filepond" id="" />
  </main>
</template>

<script setup lang="ts">
import { onMounted, ref } from 'vue'
import * as filepond from 'filepond'
import type { FilePond } from 'filepond'
import 'filepond/dist/filepond.min.css'

const fileInput = ref<HTMLInputElement | null>(null)
const pond = ref<FilePond | null>(null)

const init = () => {
  if (fileInput.value) {
    pond.value = filepond.create(fileInput.value)
    pond.value.setOptions({
      server: 'http://127.0.0.1:3000/upload',
      chunkUploads: true,
      chunkSize: 10000
    })
  }
}

onMounted(() => {
  init()
})
</script>
