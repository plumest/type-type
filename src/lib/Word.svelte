<script lang="ts">
  export let word: string;
  export let typedWord: string;

  let renderWord: string = word + typedWord.slice(word.length);

  function isVowelBeforeToneMarks(index: number): boolean {
    if (renderWord.length < 2) {
      return false;
    }
    if (
      ["ิ", "ี", "ึ", "ื", "ั", "ํ", "ำ"].includes(renderWord[index - 1]) &&
      ["่", "้", "๊", "๋", "์"].includes(renderWord[index])
    ) {
      return true;
    }
    return false;
  }
</script>

<p class="word">
  {#each renderWord as text, index}
    {#if typedWord.length <= index}
      <letter class:tonemarks={isVowelBeforeToneMarks(index)}>{text}</letter>
    {:else if index >= word.length}
      <letter class:tonemarks={isVowelBeforeToneMarks(index)} class="extra"
        >{text}</letter
      >
    {:else}
      <letter
        class:tonemarks={isVowelBeforeToneMarks(index)}
        class={word[index] === typedWord[index] ? "active" : "incorrect"}
        >{text}</letter
      >
    {/if}
  {/each}
</p>

<style lang="scss">
  @import "../styles/colors.scss";

  .word {
    position: relative;
    display: inline-flex;
    margin: 4px;
    user-select: none;
    transition: all 0.25s ease;

    letter {
      cursor: default;
      position: relative;
      color: $sub-color;
      font-size: 24px;
    }

    .active {
      color: $text-color;
    }

    .incorrect {
      color: $error-color;
    }

    .extra {
      color: $extra-error-color;
    }

    .tonemarks {
      top: -6px;
    }
  }
</style>
