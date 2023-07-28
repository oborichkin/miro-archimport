<script lang="ts">
export default {
  data() {
    return {

    }
  },
  methods: {
    loadXml(event: Event) {
      const target = event.target as HTMLInputElement
      if (!target.files) return console.log("Unexpected error")

      let file = target.files[0]

      let reader = new FileReader()
      let parser = new DOMParser()

      reader.readAsText(file)

      reader.onload = function () {
        let xmlDoc = parser.parseFromString(reader.result as string, "text/xml")
        console.log(xmlDoc)
      }

      reader.onerror = function () {
        console.log(reader.error)
      }
    }
  }
}
</script>

<template>
  <div id="root">
    <div class="grid wrapper">
      <div class="cs1 ce12">
        <input type="file" @change="loadXml" accept="*/*">
      </div>
    </div>
  </div>
</template>

<style></style>
