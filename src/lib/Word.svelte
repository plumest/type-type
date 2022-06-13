<script lang="ts">
  export let word: string;
  export let typedWord: string;

  let renderWord: string = word + typedWord.slice(word.length);
</script>

<p class="word">
  {#each renderWord as text, index}
    {#if typedWord.length <= index}
      <letter class="">{text}</letter>
    {:else}
      <letter class={word[index] === typedWord[index] ? "active" : "incorrect"}
        >{text}</letter
      >
    {/if}
  {/each}
</p>

<style lang="scss">
  @import "../styles/colors.scss";

  .word {
    display: inline-block;

    letter {
      color: $sub-color;
      font-size: 24px;
    }

    .active {
      color: $text-color;
    }

    .incorrect {
      color: $error-color;
    }
  }
</style>
