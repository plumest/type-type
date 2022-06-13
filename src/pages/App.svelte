<script lang="ts">
  import Layout from "../lib/__layout.svelte";

  import Word from "../lib/Word.svelte";
</script>

<Layout>
  <div class="word-container">
    <div class="words">
      <Word word="text" typedWord="texted" />
      <Word word="text" typedWord="te" />
      <Word word="text" typedWord="tesdf" />

      <Word word="ดูหมิ่น" typedWord="ดูหมิ่น" />
      <Word word="ดูหมิ่น" typedWord="ดูหมิ" />
      <Word word="ดูหมิ่น" typedWord="ดุหมิ้อห" />
    </div>
  </div>
</Layout>

<style lang="scss">
  .word-container {
    display: grid;
    margin: auto;
    text-align: center;
  }
</style>
